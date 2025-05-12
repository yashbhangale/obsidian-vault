### 1. Vanilla Autoencoder
![[Pasted image 20250512162234.png]]

Vanilla Autoencoder is a simple yet powerful framework for ==unsupervised learning tasks==. It comprises of two primary components: an ==encoder and a decoder==. Together these components function together compress input data into a lower-dimensional representation and then reconstruct it.

- Training a Vanilla **==Autoencoder involves minimizing the reconstruction error which find the difference between the input data and the reconstructed output==**.
- This is typically achieved through a process known as ==backpropagation== where gradients of the reconstruction error with respect to the model parameters are computed and used to update the weights of the neural network layers. The objective is to optimize the parameters such that the reconstructed output closely matches the original input.

****Applications of Vanilla Autoencoders****

Vanilla Autoencoders are simple yet powerful and are used in various fields. Some key applications include:

- ****Data Compression:**** They learn a compact version of the input data making storage and transmission more efficient.
- ****Feature Learning:**** It extract important patterns from data which is useful in image processing, natural language processing and sensor analysis.
- ****Anomaly Detection:**** If the reconstructed output is different from the original input, it can indicate an anomaly or outlier, making autoencoders useful for fraud detection and system monitoring.



