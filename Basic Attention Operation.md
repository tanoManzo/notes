As you've learned, attention allows a seq2seq decoder to use information from each encoder step instead of just the final encoder hidden state. In the attention operation, the encoder outputs are weighted based on the decoder hidden state, then combined into one context vector Bhadanau, et al (2014).

## 1: Calculating alignment scores

The first step is to calculate the alignment scores. This is a measure of similarity between the decoder hidden state and each encoder hidden state. From the paper, this operation looks like

$$
\large e_{ij} = v_a^\top \tanh{\left(W_a s_{i-1} + U_a h_j\right)}
$$

where $W_a \in \mathbb{R}^{n\times m}$, $U_a \in \mathbb{R}^{n \times m}$, and $v_a \in \mathbb{R}^m$
are the weight matrices and $n$ is the hidden state size. In practice, this is implemented as a feedforward neural network with two layers, where $m$ is the size of the layers in the alignment network. 

![[Pasted image 20230629135404.png]]


## 2: Turning alignment into weights

The next step is to calculate the weights from the alignment scores. These weights determine the encoder outputs that are the most important for the decoder output. These weights should be between 0 and 1, and add up to 1. You can use the softmax function (which I've already implemented above) to get these weights from the attention scores. Pass the attention scores vector to the softmax function to get the weights. Mathematically,

$$
\large \alpha_{ij} = \frac{\exp{\left(e_{ij}\right)}}{\sum_{k=1}^K \exp{\left(e_{ik}\right)}}
$$



## 3: Weight the encoder output vectors and sum

The weights tell you the importance of each input word with respect to the decoder state. In this step, you use the weights to modulate the magnitude of the encoder vectors. Words with little importance will be scaled down relative to important words. Multiply each encoder vector by its respective weight to get the alignment vectors, then sum up the weighted alignment vectors to get the context vector. Mathematically,

$$
\large c_i = \sum_{j=1}^K\alpha_{ij} h_{j}
$$