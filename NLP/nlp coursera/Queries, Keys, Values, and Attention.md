![[Pasted image 20240327161710.png]]
Similarity between words is called alignment

## Scale dot-product attention
![[Pasted image 20240327161853.png]]
![[Pasted image 20240327161903.png]]
![[Pasted image 20240327161915.png]]
![[Pasted image 20240327161923.png]]
![[Pasted image 20240327162143.png]]

```python
def softmax(x, axis=0):
    """ Calculate softmax function for an array x
    
        axis=0 calculates softmax across rows which means each column sums to 1 
        axis=1 calculates softmax across columns which means each row sums to 1
    """
    y = np.exp(x) 
    return y / np.expand_dims(np.sum(y, axis=axis), axis)

def calculate_weights(queries, keys):
    """ Calculate the weights for scaled dot-product attention"""
    dot = np.matmul(queries, keys.T)/np.sqrt(keys.shape[1])
    weights = softmax(dot, axis=1)
    
    assert weights.sum(axis=1)[0] == 1, "Each row in weights must sum to 1"
    
    return weights

def attention_qkv(queries, keys, values):
    """ Calculate scaled dot-product attention from queries, keys, and values matrices """
    weights = calculate_weights(queries, keys)
    return np.matmul(weights, values)
```

#nlp #attention 