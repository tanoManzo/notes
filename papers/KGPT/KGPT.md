# Knowledge-Grounded Pre-Training for Data-to-Text Generation

**The goal is to solve the task of Natural language generation (NLG)**

# Context of study
Data-to-Text Generation: Generating text from structured data/knowledge

**Diverse Forms of Structured Knowledge**
- [[E2ENLG]]: generate response from dialog act
- [[WebNLG]]: generate description from RDF triples (Resource Description Framework)
- [[WikiBio]]: generate biography from info-box
- TOTTO: generate sentences from multi-row table

Metric: *Bilingual Evaluation Understudy or BLUE [Papineni et al.](https://aclanthology.org/P02-1040.pdf)from IBM Watson Research Center.*   

**BLEU-4 for NLG**
![[Untitled.png]]

**Limitations**
 1. no unified model to solve all these tasks (one model per task according to SOTA)
 2. different models have weak generalization (out of vocabulary entities, unseen relations, etc.)
 3. rely on large amount of annotation, not suitable for few-shot settings

Can we use some pre-trained model such as GPT-2, BART, T5? No.
- GPT-2 is not encoder-decoder architecture
- BART, T5's encoders are not designed to encode structured knowledge

# Proposal 

Pre-trained paradigm: **Knowledge-Grounded Language Pre-trained**

**Contributions**
1. Universalize the knowledge representation: 
	- *unify knowledge triples, attribute-value pairs, infobox, tables into unified graph representation*
		node --> entity/value/topic
		edge --> relation/attribute/table header

		Example WebNLG: 
		![[Pasted image 20221011115643.png]]
		Example E2ENLG: 
		![[Pasted image 20221011115457.png]]
		Example WikiBio:	
		![[Pasted image 20221011115911.png]]

	- *data-2-text generation tasks modeled as graph-to-text problem*
		graph to text model using GNN-based Encoder + Transformer Decoder
		
		- GNN-based Encoder
			1. Map the lexicons of all the head tailed entities and relations into their vector representation
			 ![[Pasted image 20221011124040.png]] 
			2. head-tail entities and the relations are  aggregated into a triple representation
			![[Pasted image 20221011124253.png]]
			3. different triples sharing the same head entities are aggregated into a entity representation 
				![[Pasted image 20221011124530.png]]
			1. different entities are aggregated into factor representation
				![[Pasted image 20221011124941.png]]
		
		- Transformer Decoder  
			After encoder we have sequences of representations over all the nodes and edges. Transformer decoder with copy mechanism to generate the final text token by token
			![[Pasted image 20221011125644.png]]	
2. Pretrain a large model on a knowledge-grounded text corpus
	- Construct Pseudo Graph-to-Text Pairs
		- WikiData (Knowledge Graph)
		- Wikipedia (text)
		- WikiData (Hyperlink<-->Wikipedia)
		![[Pasted image 20221011142832.png]]
	- Data selection	
		Some sentences could be not relevant to the case. 	
		Lexical Overlap
		![[Pasted image 20221011142904.png]]
		![[Pasted image 20221011144024.png]]
3. Fine-tune on downstream data-to-text task with only a few examples
	- Pre-training the model on the KGText dataset
		![[Pasted image 20221011144236.png]]
	- fine-tune on the downstream task to solve individual problems 
		![[Pasted image 20221011144546.png]]
	
The KGLP model can achieve nearly the same performance with as few as 100 samples. 

# Results 

**Dataset**
- E2ENLG (Dialog Act)
- WebNLG (RDF Triple)
- WikiBio (Table)

**Setting** 
Two types of encoder Graph-encoder and Sequential-encoder, both encoding schemes with a copy mechanism without copy loss.
- Fully-Supervised 
	![[Pasted image 20221011162424.png]]
- Few-Shot
	![[Pasted image 20221011163011.png]]
- Zero-shot
	![[Pasted image 20221011163254.png]]

- Human evaluation
![[Pasted image 20221012153758.png]]

**Conclusion**
KGPT performs better than GPT-2 based models 
- fewer compute resources for pre-training. 
- pretraining boost few-shots performance task
- strong generalization to understand unseen knowledge inputs