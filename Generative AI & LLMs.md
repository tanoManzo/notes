 Generative AI is a subset of traditional ML. ML models that underpinned  learn the statistical pattern of the data.

## Fundation (Base) Models 

![[Pasted image 20240712102759.png]]

more parameters = more memory

![[Pasted image 20240712104321.png]]

The output of the model is called a **completion**. The act of using the model to generate text is known as inference. 

![[Pasted image 20240712104924.png]]

Generative algorithms are not new, Recurrent Neural Networks.
![[Pasted image 20240712105236.png]]

![[Pasted image 20240712105248.png]]

![[Pasted image 20240712105409.png]]
![[Pasted image 20240712105443.png]]
## Transformer Architecture
![[Pasted image 20240712105548.png]]
![[Pasted image 20240712105638.png]]
![[Pasted image 20240712105659.png]]
![[Pasted image 20240712105717.png]]
How the model works?

![[Pasted image 20240712105746.png]]

![[Pasted image 20240712105839.png]]

Now, machine-learning models are just big statistical calculators and they work with numbers, not words. So before passing texts into the model to process, you must first tokenize the words. Simply put, this converts the words into numbers, with each number representing a position in a dictionary of all the possible words that the model can work with. You can choose from multiple tokenization methods. 

![[Pasted image 20240712105858.png]]

Now that your input is represented as numbers, you can pass it to the embedding layer. This layer is a trainable vector embedding space, a high-dimensional space where each token is represented as a vector and occupies a unique location within that space. Each token ID in the vocabulary is matched to a multi-dimensional vector, and the intuition is that these vectors learn to encode the meaning and context of individual tokens in the input sequence.

![[Pasted image 20240712105912.png]]

From the Transformer paper
![[Pasted image 20240712110252.png]]

In case of 3 dimension per embedding: 
![[Pasted image 20240712110409.png]]

Positional Encoding to preserve the word order (because everything append in parallel). So by adding the positional encoding to the token embeddings you preserve the information and don't lose the relevance of the position of the words in the sentence. 

![[Pasted image 20240712110511.png]]

The model analyzes the relationships between the tokens in your input sequence. As you saw earlier, this allows the model to attend to different parts of the input sequence to better capture the contextual dependencies between the words. The self-attention weights that are learned during training and stored in these layers reflect the importance of each word in that input sequence to all other words in the sequence. But this does not happen just once, the transformer architecture actually has multi-headed self-attention. This means that multiple sets of self-attention weights or heads are learned in parallel independently of each other. 

![[Pasted image 20240712112028.png]]
The number of attention heads included in the attention layer varies from model to model, but numbers in the range of 12-100 are common. The intuition here is that each self-attention head will learn a different aspect of language. For example, one head may see the relationship between the people entities in our sentence. Whilst another head may focus on the activity of the sentence. Whilst yet another head may focus on some other properties such as if the words rhyme. It's important to note that you don't dictate ahead of time what aspects of language the attention heads will learn. The weights of each head are randomly initialized and given sufficient training data and time, each will learn different aspects of language.

![[Pasted image 20240712112141.png]]

The output is processed through a fully connected feed-forwad network. The output of this layer is a vector of logits proportional to the probability score to each and every token in the tokenizer dictionary.

![[Pasted image 20240712112417.png]]


Those logits are pass to a softmax layer, where they are normalized into a probability score for each word. 

![[Pasted image 20240712112508.png]]

The output is a probability for every single word in the vocabolary. So there is likely to be thousands of scores. One single token will have the score higher than the rest. **This is the most likely predicted token.**

## Example End-2-End Translation
![[Pasted image 20240716112531.png]]

1) Tokenizer

![[Pasted image 20240716112719.png]]

2) Embedding Layer + Encoder Layer (Multi-head attention layers)

![[Pasted image 20240716113036.png]]

3) The output of the multi-head attention is injected into the feed-forward NN to the output of the encoder.
4) At this point, the data that leaves the encoder is a deep representation of the structure and the meaning of the input sequence. This is inserted into the middle of the Decoder (i.e., self-attention of the decoder):![[Pasted image 20240716113318.png]]
5) Decode, a start of sequence token is added to the input of the decoder trigging the decoder to predict the next token. It does this besed on the contextual understanding (output of the encoder to the decoder).![[Pasted image 20240716113747.png]]
6) The output of the decoder passes throw the decoder feed-forward NN and a final softmax output layer. ![[Pasted image 20240716113914.png]]
7) Here we have the first token, we can continue by using it as input to the decoder for the prediction of the next token.  ![[Pasted image 20240716114113.png]]
8) The final sequence of token can be de-tokenized into words![[Pasted image 20240716114211.png]]
### In summary: 
	![[Pasted image 20240716114258.png]]
#### Encoder (input and output same length): ![[Pasted image 20240716114436.png]]
	You can try encoder-only model to perform classification task such as sentiment analysis. BERT is an example of an encoder-only model. 
	
#### Encoder-Decoder Model 
	![[Pasted image 20240716114619.png]]
	Sequence to Sequence tasks such as translation where the input sequence and the output sequence can be different lengths. You can scale this model to do generation tasks. BART and T5 are example of this architecture. 
	
##### Decoder-only model, most common used. 
		GPT, BLOOM, Llama and more. 
		
The multi-head self-attention mechanism allows the model to attend to different parts of the input sequence, while the feed-forward network applies a point-wise fully connected layer to each position separately and identically. The Transformer model also uses residual connections and layer normalization to facilitate training and prevent overfitting. In addition, the authors introduce a positional encoding scheme that encodes the position of each token in the input sequence, enabling the model to capture the order of the sequence without the need for recurrent or convolutional operations.

## Prompting and prompt engineering

The input is called prompt, the act of generating text is know as inference, the output of the model is called completion.
The context window is where you type the prompt and it appears as output at the begging. 

#### in-context learning (ICL)
When the user provides the example inside the context window. 
![[Pasted image 20240716144613.png]]

![[Pasted image 20240716144720.png]]
![[Pasted image 20240716144825.png]]
![[Pasted image 20240716144839.png]]

### Parameters 
![[Pasted image 20240716145119.png]]

![[Pasted image 20240716145213.png]]
![[Pasted image 20240716145259.png]]
be careful with repetitions. Instead random sampling is more creative:
![[Pasted image 20240716145349.png]]
Top-K based on the probability, then random.
![[Pasted image 20240716145451.png]]
Top-p based on the probability threshold, then random. 
![[Pasted image 20240716145543.png]]
Temperature controls randomness
![[Pasted image 20240716145654.png]]
![[Pasted image 20240716145953.png]]

## Generative AI Project Lifecycle
![[Pasted image 20240717143614.png]]
- Scope: as narrow as possible. For instance: ![[Pasted image 20240717143741.png]]
- Select: work with existing model or train from scratch
- Adapt and align mode: assess the performance of the chosen model on the assigned task(s) ![[Pasted image 20240717144240.png]]
- Application Integration: Optimize and deploy, additional infrastructure. 

## Model Hubs
![[Pasted image 20240723133859.png]]

### Pre-training 
LLMs capture a deep statistical representation of language. 
![[Pasted image 20240723134126.png]]

![[Pasted image 20240723134142.png]]
![[Pasted image 20240723134157.png]]

![[Pasted image 20240723134236.png]]

![[Pasted image 20240723134252.png]]

![[Pasted image 20240723134306.png]]

![[Pasted image 20240723134345.png]]
![[Pasted image 20240723134354.png]]
![[Pasted image 20240723134401.png]]
![[Pasted image 20240723134427.png]]
![[Pasted image 20240723134439.png]]
![[Pasted image 20240723134456.png]]
![[Pasted image 20240723134506.png]]
![[Pasted image 20240723134516.png]]
![[Pasted image 20240723134528.png]]
![[Pasted image 20240723134620.png]]
![[Pasted image 20240723134736.png]]

## Computational Challenges

#### Out of Memory 
![[Pasted image 20240723134853.png]]
Compute Unified Device Architecture

![[Pasted image 20240723135224.png]]

![[Pasted image 20240723135325.png]]
![[Pasted image 20240723135350.png]]
![[Pasted image 20240723135434.png]]
![[Pasted image 20240723135452.png]]
![[Pasted image 20240723135553.png]]
![[Pasted image 20240723135605.png]]
![[Pasted image 20240723135633.png]]
![[Pasted image 20240723135656.png]]
![[Pasted image 20240723135713.png]]
![[Pasted image 20240723135741.png]]
![[Pasted image 20240723135809.png]]
![[Pasted image 20240723135924.png]]
![[Pasted image 20240723135937.png]]
![[Pasted image 20240723140003.png]]
![[Pasted image 20240723140022.png]]
![[Pasted image 20240723140109.png]]
![[Pasted image 20240723140126.png]]
![[Pasted image 20240723140215.png]]
### Multiple GPUs

#### When the model and all the parameters fit into a single gpu and you want to parallelize it
 ![[Pasted image 20240821164720.png]]
 ![[Pasted image 20240821164736.png]]
#### When your model and all the parameters do not fit into a single gpu
![[Pasted image 20240821164902.png]] 

Share data among several gpus with no overlaps. 
![[Pasted image 20240821165027.png]]
Without Zero, the model and all the parameters would be copied on each gpu (Baseline, plot below). With ZeRO, just the parameter concerning the data of the specific gpu (Pos, plot below). Zero 1 parallelizes only the optimizer parameters, Zero 3 parallelizes everything 

![[Pasted image 20240821165137.png]]

Full share of parameters  
![[Pasted image 20240821165535.png]]

With ZERO
![[Pasted image 20240821165705.png]]
![[Pasted image 20240821165735.png]]
![[Pasted image 20240821165915.png]]
![[Pasted image 20240821170023.png]]
![[Pasted image 20240821170040.png]]

### Scaling Laws
![[Pasted image 20240821170516.png]] 
![[Pasted image 20240821170606.png]]
![[Pasted image 20240821170657.png]]