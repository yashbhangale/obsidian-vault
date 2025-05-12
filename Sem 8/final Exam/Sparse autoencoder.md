
![[Pasted image 20250512162538.png]]

[Sparse Autoencoder](https://www.geeksforgeeks.org/sparse-autoencoders-in-deep-learning/) are a type of autoencoder that ==encourage only a few neurons to activate in the hidden layer creating a sparse and efficient representation of the data==. _Unlike regular autoencoders that focus only on reconstruction sparse autoencoders add constraints to enforce sparsity._

**How They Work:***

- ****Regularization:**** Methods like L1 regularization (penalizing large weights) and dropout (randomly turning off neurons) help enforce sparsity.
- ****KL Divergence:**** This measures the difference between two distributions and is used to ensure the latent representation remains sparse by matching a predefined sparse target.

Sparse autoencoders are useful for feature selection and learning meaningful patterns while reducing unnecessary activations.

