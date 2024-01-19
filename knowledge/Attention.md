![[Pasted image 20240119094305.png]]
![[Pasted image 20240119094620.png]]
## General 
![[Pasted image 20231016173102.png]]

Recall that in scale dot-products attention, you have queries, keys and values. The attention layer outputs contacts vectors for each query. And the context vectors are weighted sums of the values where the similarity between the queries and keys determines the weights assigned to each value.
Play video starting at ::42 and follow transcript0:42
The SoftMax ensures that the weights add up to 1 and the division by the square roots of the dimension of the key factors is used to improve performance.


![[Pasted image 20231016173547.png]]


![[Pasted image 20231016174021.png]]
![[Pasted image 20240119095016.png]]
![[Pasted image 20240119100043.png]]
![[Pasted image 20240119100303.png]]
![[Pasted image 20240119100604.png]]
![[Pasted image 20240119100833.png]]
![[Pasted image 20231016174102.png]]



## Type of Attention

![[Pasted image 20231030162023.png]]

![[Pasted image 20231030162127.png]]

![[Pasted image 20231030162216.png]]
This is present in the decoder transformer model and it makes sure that prediction at each prediction depends only on the known output.
![[Pasted image 20231030162538.png]]

![[Pasted image 20231030162811.png]]
![[Pasted image 20231030163840.png]]

## Multi-head Attention

![[Pasted image 20231030163107.png]]

The number of columns in Q, K, and V is the embedding size. The number of rows is given by the number of words the sequence has used to construct each metrix.
![[Pasted image 20231030163305.png]]

![[Pasted image 20231030163520.png]]


d<sub>k</sub> and d<sub>v</sub> are recommended to be d<sub>model</sub>/d<sub>h</sub> for performance reason in comparison to the single head model. 
![[Pasted image 20231030163935.png]]
![[Pasted image 20231030164014.png]]

![[Pasted image 20231030173404.png]]

![[Pasted image 20231030173459.png]]


## Dot product attention

Here we come to the crux of this lab, in which we compute 
$\textrm{softmax} \left(\frac{Q K^T}{\sqrt{d}} + M \right) V$, where the (optional, but default) scaling factor $\sqrt{d}$ is the square root of the embedding dimension.

![[Pasted image 20231030174041.png]]
![[Pasted image 20231030174358.png]]

![[Pasted image 20231101131807.png]]

![[Pasted image 20231101132656.png]]