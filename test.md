```mermaid
graph TD
  A[Backpropagation] -->|Supervised learning with optimization algorithm (e.g., gradient descent)| B[Gradient Descent]
  B -->|Chain rule applied during backpropagation. Gradients calculated layer by layer| C[Vanishing Gradient]
  C -->|Gradients become very small during backpropagation. Sigmoid/tanh can lead to close-to-zero gradients.| D[Impact on Training]
  D -->|Small gradients result in small weight updates. Network struggles to learn long-range dependencies.| E[Mitigating Strategies]
  E -->|Use ReLU, Leaky ReLU, PReLU, or ELU activation functions.| E
  E -->|Implement batch normalization.| E
  E -->|Explore architectures with skip/residual connections.| E
