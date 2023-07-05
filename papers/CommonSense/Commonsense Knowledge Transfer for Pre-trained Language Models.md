
Wangchunshu Zhou, Ronan Le Bras, Yejin Choi

## Abstract
Commonsense knowledge transfer, a framework to transfer the
commonsense knowledge stored in a neural commonsense knowledge model to a general purpose pre-trained language model. 

## Intro
Self-supervised pre-training objectives including masked language modeling (Devlin et al.,2019) and masked span infilling (Lewis et al., 2020) enable pre-trained models to acquire linguistic (Hewitt and Manning, 2019; Manning et al., 2020) and factual knowledge (Petroni et al., 2019) by modeling the distribution of naturally occurring texts.

However, most of these objectives are limited to exploiting the surface form of human language, and the lack of grounded supervision calls into question how well these representations can ever capture meaning (Bender and Koller, 2020), not to mention the underlying commonsense knowledge which is often reasoned implicitly and does not appear in the surface form of human language (Merrill et al., 2021; Zhou et al., 2020a; Hwang et al., 2021). On the other hand, commonsense reasoning is important for building generalizable models because it enables the model to reason about a great number of events, causes, and effects, while observing only a small fraction of them

Two distinct lines of research focus on improving commonsense reasoning ability of pre-trained language models.
1. Incorporate external commonsense knowledge graph for commonsense reasoning (Lin et al., 2019; Liu et al., 2021; Cui and Chen, 2021). 
2. **Inject commonsense knowledge into the parameters of pretrained models (Li et al., 2019; Zhou et al., 2021; Klein and Nabi, 2021).**

Commonsense knowledge transfer is conceptually related to knowledge distillation (KD) (Hinton et al., 2015) since they both aim to transfer knowledge from a knowledge-rich model to another model that lacks it. However, in the latter the source model and the target model are heterogeneous because they are trained on different data with different objectives. Instead of simply mimicking the teacher model, commonsense knowledge transfer requires the target model to learn specialized knowledge from the source model while retaining its own capability.

We propose to first extract commonsense knowledge in textual form from the source model and then exploit the extracted knowledge to form self-supervised training data for the target model.

![[Pasted image 20230627162059.png]]

## Methodology
Our proposed commonsense knowledge transfer framework consists of a neural commonsense knowledge model (e.g., COMET) and a pre-trained model (e.g., T5).


### Commonsense Knowledge Extraction 
We first describe the source model, i.e., neural commonsense knowledge model, in the commonsense knowledge transfer framework. It is a transformer (Vaswani et al., 2017) language model trained on commonsense knowledge graphs like ATOMIC (Sap et al., 2019a) and ConceptNet (Speer et al., 2017) with the objective of predicting the object (i.e., commonsense inference) with the subject (i.e., natural text) and relation as input. For example, given a commonsense tuple (s=“take a nap", r=Causes, o=“have energy"), the neural commonsense knowledge model is trained to generate o given s and r as inputs.

To extract commonsense knowledge stored in a neural commonsense knowledge model, we use a natural sentence as the subject s (e.g., he wants to cook a meal) and concatenate it with a randomly selected commonsense relation r (e.g., xNeed) from a pre-defined set to form a prompt (e.g., he wants to cook a meal xNeed ). We then feed the prompt to the neural commonsense knowledge model and use it to generate a commonsense inference (e.g., to buy ingredients).

### Commonsense Knowledge Injection
we propose two commonsense-related self-supervised objectives: *commonsense text infilling and commonsense relation prediction.* 

![[Pasted image 20230627175231.png]]

**Commonsense text infilling** is a simple extension to the conventional text infilling objective used for pre-training BART and T5. It transforms each sentence to a commonsense tuple similar to that in a commonsense knowledge graph by appending the commonsense relation and the generated commonsense inference. We then mask text spans in the commonsense tuple by randomly selecting one masking scheme among text masking, commonsense masking, bidirectional masking, and relation masking. We then train the model to predict the masked spans autoregressively. The diverse masking strategies provide more diverse training signals compared to random masking, thus enabling the model to better align the surface form of human language and the underlying commonsense knowledge. Tokens recognized as nouns or verbs by a Spacy POS tagger with a higher probability so that the model will be trained to predict concepts more frequently compared to non-content words that are generally not related to commonsense reasoning.



While the commonsense text infilling objective encourages the pre-trained model to align natural texts and their commonsense inferences, it is always trained on valid commonsense tuples. This can be suboptimal because we also want the model to be capable of discriminating invalid commonsense inferences, which is important for many commonsense related downstream tasks.

**Commonsense Relation Prediction** task trains the model to distinguish the correct commonsense inference corresponding to the input sentence and the commonsense relation from distractors.

![[Pasted image 20230627180223.png]]
the commonsense relation prediction objective is formulated as a multi-choice QA problem with an input sentence as the context, a commonsense relation as the question, and a set of four commonsense inferences as options. The set of options
consists of one correct commonsense inference, which is generated by the neural commonsense model with the input sentence and commonsense relation as input, and three carefully curated distractors (i.e., negative examples) generated by the
same neural commonsense knowledge model with different inputs.

## Experiments
We use COMET-ATOMIC, a state-of-the-art neural commonsense knowledge model that can generate accurate, representative knowledge for new, unseen entities and events, as the source model. It is initialized with BART and continually trained on ATOMIC (Hwang et al., 2021), a new general purpose commonsense knowledge graph.

![[Pasted image 20230627181251.png]]
We evaluate the continual pre-trained models on downstream tasks that require commonsense reasoning including CommonsenseQA (Talmor et al., 2018), OpenbookQA (Mihaylov et al., 2018), PIQA (Bisk et al., 2020), aNLI (Bhagavatula et al., 2020), COPA (Roemmele et al., 2011), and SOCAILIQA (Sap et al., 2019b) In addition to the conventional fully supervised setting, we also test our approach in the few-shot setting by varying the percentage of labeled examples from the original training set used for fine-tuning.

**Impact of Objectives** We find that both the proposed objectives contribute to the performance improvement of our approach. The commonsense text infilling objective is shown to be more critical than the commonsense relation prediction task. We suspect this is because commonsense text infilling resembles the vanilla text infilling objective with which the T5 models are pre-trained, thus preventing the model from catastrophic forgetting. In addition, all four masking strategies are beneficial, and their contribution varies for different downstream tasks. This confirms the necessity of a diverse masking scheme. Moreover, our strategy for constructing distractors outperforms the random counterpart, demonstrating the necessity of hard negative examples for the commonsense relation prediction task. 

**Multi-task versus Sequential Transfer** As for the training order between the two objectives, we find that starting from the commonsense text infilling task and then switching to the commonsense relation prediction task performs similarly with our
multi-tasking strategy while significantly outperforming its counterpart training with the reverse direction. We think this is because the commonsense text infilling objective resembles the original pre-training while the commonsense relation prediction is more similar to downstream tasks. We opt for the multi-tasking strategy for simplicity.

**Impact of Corpus Size** We find that commonsense knowledge transfer significantly outperforms both the T5 baseline and the competitive CALM method with only 10 percent of the full data used for distillation. Nevertheless, the performance improvement also confirms that our approach can benefit from the accessibility of large-scale natural texts. For base-size models, the performance improvements seem to saturate after 10 million sentence pairs. However, we anticipate that larger-size models may still benefit from a larger amount of data, and leave this for future work. 


## to lookup
- self-supervised
- commonsense inference
- distillation
- ablation
#research #llm #knowledge #good4pub 