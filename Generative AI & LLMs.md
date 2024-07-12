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

Positional Encoding to preserve the word order (because everything append in parallel). So by adding the positional encoding to the token embeddings you preserve the information and don't lose  
![[Pasted image 20240712110511.png]]