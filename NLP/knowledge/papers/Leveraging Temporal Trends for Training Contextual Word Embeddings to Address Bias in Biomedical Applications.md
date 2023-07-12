Zhang et al.[3] showed that word embeddings trained on clinical texts cause performance gaps for different genders and races on clinical tasks.

We aim to train word embeddings that (1) make use of the entire dataset of clinical trial abstracts, (2) harness the positive temporal trends in clinical trials, and (3) achieve high performance on the downstream tasks.

Existing methods to remove representational gender bias from word embeddings aim to remove sensitive information, e.g., gender, from the embeddings using data augmentation[14-15], in-training methods modifying the training objective[16], or post-training methods such as projections to subspaces[4, 17, 18].

Recently, adversarial training[3, 19, 20] was also applied to remove information about the protected attribute from the representations. These methods aim for a notion of fairness named demographic parity[21]: an independence between a model's prediction and the protected attribute. Indeed, a decision model cannot use the protected attribute if it is not recoverable from the embeddings. However, in the clinical domain, demographic parity should not be applied, since the sensitive attribute (e.g., gender) is an important feature in clinical prediction tasks.

In this work we aim to achieve another notion of fairness -- equalized odds[22]: an independence between a model's prediction and a sensitive attribute given the true label. Equalized odds in the clinical domain translates to achieving similar performance in clinical downstream tasks over different demographic groups (men and women).

We present DERT -- a framework for Debiasing Embeddings through Regularization with Temporal distribution matching. In this framework, a regularization term is added to the training process, to capture the temporal distribution matching. To that end, we propose a novel use of the GAN framework, where the generator is an embedding model, and the discriminator is a classifier which aims to distinguish older from newer samples based on their embedding. The competition between the two components acts as a temporal distribution matching mechanism. While there are methods to tackle model biases directly, in this work we explore the effects of temporal regularization on bias.

In this work we describe DERT, a framework for Debiasing Embeddings by Regularization with Temporal distribution matching. We train word embeddings on PubMed abstracts describing clinical trials between 2010-2018. To harness the temporal trends in clinical trials, we require that the distribution of embeddings of the older abstracts will be similar to that of newer abstracts. To achieve this, in addition to training the embedding model on the original semantic task, we simultaneously train it on a temporal classification task. The abstracts are divided to old and new and assigned a temporal label. A classifier aims to distinguish old from new abstracts based on their embeddings, while the embedding model aims to reduce the classifier’s performance by tuning the embeddings.

1. not sure about the contribution
2. not motivated GAN
3. figure in the appendix, can be improved, some terms not explained such as Theta. 
4. not clear Temporal Discriminator
5. Model poorly explained 
