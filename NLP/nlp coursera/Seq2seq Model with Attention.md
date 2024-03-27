![[Pasted image 20240319095939.png]]

## with and without Attention

![[Pasted image 20240319101615.png]]

## weighted sum based on the step (most imp words) and context vector for decoder

![[Pasted image 20240319113407.png]]

Context vector and weights

![[Pasted image 20240319113606.png]]
## exercise

![[Pasted image 20240319114150.png]]


### get alignment score: similarity between the decoder hidden state and each of the encoder hidden state 
```
hidden_size = 16
attention_size = 10
input_length = 5

np.random.seed(42)

# Synthetic vectors used to test
encoder_states = np.random.randn(input_length, hidden_size)
decoder_state = np.random.randn(1, hidden_size)

# Weights for the neural network, these are typically learned through training
# Use these in the alignment function below as the layer weights
layer_1 = np.random.randn(2 * hidden_size, attention_size)
layer_2 = np.random.randn(attention_size, 1)

# Implement this function. Replace None with your code. Solution at the bottom of the notebook
def alignment(encoder_states,decoder_state):
    # First, concatenate the encoder states and the decoder state
    inputs = np.concatenate((encoder_states, decoder_state.repeat(input_length, axis=0)), axis=1)
    assert inputs.shape == (input_length, 2 * hidden_size)
    
    # Matrix multiplication of the concatenated inputs and layer_1, with tanh activation
    activations = np.tanh(np.matmul(inputs, layer_1))
    assert activations.shape == (input_length, attention_size)
    
    # Matrix multiplication of the activations with layer_2. Remember that you don't need tanh here
    scores = np.matmul(activations, layer_2)
    assert scores.shape == (input_length, 1)
    
    return scores
```

### get context vector:  weight of the encoder output vectors and sum

![[Pasted image 20240319121704.png]]

```
# Implement this function. Replace None with your code.
def attention(encoder_states, decoder_state):
    """ Example function that calculates attention, returns the context vector 
    
        Arguments:
        encoder_vectors: NxM numpy array, where N is the number of vectors and M is the vector length
        decoder_vector: 1xM numpy array, M is the vector length, much be the same M as encoder_vectors
    """ 
    
    # First, calculate the alignment scores
    scores = alignment(encoder_states, decoder_state)
    
    # Then take the softmax of the alignment scores to get a weight distribution
    weights = softmax(scores)
    
    # Multiply each encoder state by its respective weight
    weighted_scores = encoder_states*weights
    
    # Sum up weighted alignment vectors to get the context vector and return it
    context = sum(weighted_scores)
    return context

context_vector = attention(encoder_states, decoder_state)
print(context_vector)
```
The sequential nature of models you learned in the previous course (RNNs, LSTMs, GRUs) does not allow for parallelization within training examples, which becomes critical at longer sequence lengths, as memory constraints limit batching across examples. In other words, if you rely on sequences and you need to know the beginning of a text before being able to compute something about the ending of it, then you can not use parallel computing. You would have to wait until the initial computations are complete. This is not good, because if your text is too long, then 1) it will take a long time for you to process it and 2) you will lose a good amount of information mentioned earlier in the text as you approach the end.

#nlp #attention 