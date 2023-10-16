![[Pasted image 20231016173102.png]]

Recall that in scale dot-products attention, you have queries, keys and values. The attention layer outputs contacts vectors for each query. And the context vectors are weighted sums of the values where the similarity between the queries and keys determines the weights assigned to each value.
Play video starting at ::42 and follow transcript0:42
The SoftMax ensures that the weights add up to 1 and the division by the square roots of the dimension of the key factors is used to improve performance.

![[Pasted image 20231016173311.png]]