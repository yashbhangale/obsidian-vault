**Generative models** are a class of machine learning models that **learn the underlying patterns of data** and can **generate new, similar data** based on what they’ve learned.

### In Simple Terms:

They don’t just learn to classify or predict  they **create**. For example:
- They can write essays, generate images, compose music, or create voices.
- ChatGPT is a generative model that creates human-like text.

### Types of Generative Models:

1. **Generative Adversarial Networks (GANs)**
    - Two networks compete: a generator (creates) and a discriminator (evaluates).
    - Used in deepfake creation, art generation, image enhancement.

2. [[Variational Autoencoders (VAEs)]]    
    - Encode input  data into a smaller space and decode it back.
    - Useful for image generation and data compression.

3. **Autoregressive Models (like GPT)**    
    - Predict the next item (word, pixel, etc.) based on previous items.
    - Used in text generation, like GPT-3, GPT-4.

4. **Diffusion Models**    
    - Generate data by reversing a gradual noise process.
    - Used in tools like **DALL·E 3** and **MidJourney** for image creation.

5. **Flow-based Models**:
	These models learn **invertible transformations** between data and a simple distribution (like a Gaussian).

Key Ideas:
- Transform complex data into a simpler distribution.
- The transformation is **invertible** — you can go back and forth.
- Enable **exact likelihood computation** and **sampling**.

 🔸 Examples:
- **RealNVP**
- **Glow (by OpenAI)**

 ✅ Pros:
- Exact log-likelihood.
- Efficient sampling and inference.
 ❌ Cons:
- Require invertible architectures → design limitations.


 🧩 2. **PixelRNN**

A type of **autoregressive model** designed to **generate images one pixel at a time**, row by row.
 🔹 Key Ideas:
- Predict each pixel using the pixels above and to the left.
- Uses **RNNs** (LSTM/GRU) for sequence modeling over image pixels.

 ✅ Pros:
- Captures dependencies between pixels well.    
 ❌ Cons:
- **Slow generation** — can't parallelize easily because it’s pixel-by-pixel. 
- Hard to scale to high-res images.

 🧩 3. **PixelCNN**

Same idea as PixelRNN, but replaces RNNs with **convolutional neural networks** for better parallelization.

 🔹 Key Ideas:
- Uses masked convolutions to ensure the model only "sees" previous pixels when generating the next one.

 🔸 Variants:
- **Gated PixelCNN**
- **PixelCNN++** (improved version)

 ✅ Pros:
- Faster than PixelRNN.
- Still captures pixel dependencies well.
 ❌ Cons:
- Still autoregressive — can't generate entire image in one step.
