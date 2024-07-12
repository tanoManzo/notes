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

The output is processed through a fully connected feed-forwad network. The output of this layer is a vector of logits proportional to the probability score to each and every tokem 