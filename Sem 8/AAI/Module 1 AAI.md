# **1. Types of AI Generative Models**

#### **A. Variational Autoencoders (VAEs)**

- **Probabilistic framework**: Uses deep learning to encode data into a lower-dimensional latent space and reconstructs it.
- **Latent space regularization**: Ensures meaningful interpolations between data points.
- **Reconstruction-based generation**: Generates new samples by sampling from the latent space.
- **Strengths**: Good for continuous data like images.
- **Weaknesses**: Generated samples can be blurry due to the assumption of Gaussian distribution.

#### **B. Generative Adversarial Networks (GANs)**

- **Two networks**: Consists of a **generator** (creates fake data) and a **discriminator** (distinguishes real vs. fake data).
- **Adversarial training**: Both networks compete, improving generation quality over time.
- **High-quality outputs**: Used for realistic image, video, and text generation.
- **Challenges**: Hard to train due to mode collapse (generator producing limited variations).

#### **C. Auto-Regressive Models**

- **Sequential prediction**: Predicts each data point based on previous ones.
- **Examples**: PixelCNN (image generation), GPT (text generation), transformer model.
- **High-quality output**: Captures complex patterns effectively.
- **Limitations**: Slow generation since it works sequentially.

#### **D. Flow-Based Models**

- **Invertible transformations**: Uses a sequence of invertible functions to model data distribution.
- **Exact likelihood estimation**: Unlike VAEs and GANs, they provide exact probability densities.
- **Example**: RealNVP, Glow (used for high-resolution image synthesis).
- **Strengths**: Efficient latent space sampling and reconstruction.
- **Weaknesses**: Computationally expensive due to complex transformations.

#### **E. Transformer-Based Models**

- **Self-attention mechanism**: Captures long-range dependencies in data.
- **Example**: GPT, BERT, T5 (text), DALL·E, Stable Diffusion (image).
- **Scalability**: Works well with large datasets, enabling state-of-the-art generative tasks.
- **Challenges**: Requires massive computational power and data.

---

# **2. Generative Adversarial Networks (GANs)**

#### **1. Objective Function**

![[Pasted image 20250226110047.png]]
#### **2. Training Process**

- **Step 1**: Discriminator **D** is trained to differentiate between real and generated data.
- **Step 2**: Generator **G** is updated based on how well it fools **D**.
- **Step 3**: Iteratively refine both networks until G generates highly realistic samples.

#### **3. Nash Equilibrium in GANs**

- The ideal state is when the discriminator **D** cannot distinguish between real and fake data, meaning: 
![[Pasted image 20250226110123.png]]
- At this point, **G has learned the true data distribution**, and further training does not improve performance.

#### **4. Applications**

- **Image Generation**: DeepFakes, AI art (e.g., StyleGAN, BigGAN).
- **Super-Resolution**: Enhancing image quality (SRGAN).
- **Text & Music Generation**: AI-written text, AI-composed music.

#### **5. Challenges**

- **Mode Collapse**: Generator produces limited variations.
- **Training Instability**: Finding Nash Equilibrium is difficult.
- **Vanishing Gradients**: Poor updates when D becomes too strong.

---

# **3. Detailed Comparison: VAEs vs. GANs**

| Feature                         | **VAEs (Variational Autoencoders)**                                                                                                                                                                            | **GANs (Generative Adversarial Networks)**                                                                                                                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**                  | A probabilistic generative model that learns a **latent space representation** by encoding and reconstructing data.                                                                                            | A generative model based on an **adversarial game** between two neural networks: Generator (G) and Discriminator (D).                                                         |
| **Why They Are Used**           | Used for **data compression, anomaly detection, and structured latent space learning**.                                                                                                                        | Used for **high-quality data generation**, such as images, videos, and realistic synthetic media.                                                                             |
| **Architecture**                | **Encoder-Decoder Structure**: - **Encoder** compresses input into a latent space (mean & variance). - **Decoder** reconstructs data from latent variables.                                                    | **Adversarial Model**: - **Generator (G)** maps random noise to fake data. - **Discriminator (D)** classifies real vs. fake samples.                                          |
| **Latent Space Representation** | **Structured, continuous, and regularized** using a prior distribution (Gaussian).                                                                                                                             | **Implicitly learned, unstructured**, lacks explicit regularization.                                                                                                          |
| **Training Process**            | - Encode data into latent space (mean & variance). - Sample latent vector zz using **reparameterization trick**. - Decode zz back to reconstruct input. - Optimize ELBO loss (Reconstruction + KL Divergence). | - Train **D** to classify real vs. fake samples. - Train **G** to fool **D** (i.e., generate realistic data). - Update both networks iteratively until equilibrium.           |
| **Nash Equilibrium**            | Not applicable, as VAEs are not adversarial.                                                                                                                                                                   | Reached when **D** cannot distinguish real and fake data (i.e., D(x)=0.5D(x) = 0.5 for all xx).                                                                               |
| **Loss Function**               | - **Reconstruction Loss**: Measures how well output resembles input. - **KL Divergence**: Regularizes latent space to match a prior distribution.                                                              | - **Adversarial Loss (Binary Cross-Entropy)**: Helps **D** distinguish real vs. fake samples.                                                                                 |
| **Sample Quality**              | - Outputs tend to be **blurry** due to the **Gaussian assumption** in latent space.                                                                                                                            | - Produces **high-quality, realistic images** with sharp details.                                                                                                             |
| **Mode Collapse**               | **Rare** (since latent space is well-regularized).                                                                                                                                                             | **Common** (G may learn to produce limited variations).                                                                                                                       |
| **Training Stability**          | **Stable** (due to probabilistic framework).                                                                                                                                                                   | **Unstable**, sensitive to hyperparameters, prone to **mode collapse** and **vanishing gradients**.                                                                           |
| **Computational Cost**          | **Lower**, requires less tuning and computational power.                                                                                                                                                       | **Higher**, as adversarial training needs careful hyperparameter tuning.                                                                                                      |
| **Advantages**                  | - Stable training process. - Meaningful latent space representation. - Works well for **data compression, reconstruction, and anomaly detection**.                                                             | - Generates **high-quality** and **realistic** images, videos, and text. - Powerful for **creative applications** (e.g., DeepFakes, AI art).                                  |
| **Disadvantages**               | - Outputs are often blurry. - Hard to generate sharp and realistic images.                                                                                                                                     | - Hard to train due to adversarial setup. - Mode collapse can limit diversity in generated samples.                                                                           |
| **Applications**                | - **Image Reconstruction** (denoising autoencoders, MRI scans). - **Anomaly Detection** (fraud detection, medical diagnosis). - **Data Compression** (efficient feature representations).                      | - **Image Generation** (StyleGAN, BigGAN, DeepFakes). - **Super-Resolution** (SRGAN for enhancing low-resolution images). - **Video & Music Synthesis** (AI-generated media). |

### **Conclusion**

- **VAEs** are best for **structured latent representations, reconstruction, and anomaly detection** but struggle with sample quality.
- **GANs** produce **high-quality and realistic samples**, making them ideal for **AI-generated media**, but they are harder to train.

---

# **4. Hidden Markov Model (HMM)** [[hmm hinglish]]

#### **1. Definition**

A **Hidden Markov Model (HMM)** is a **probabilistic model** used for **sequential data** where the system being modeled is assumed to follow a **Markov process** with **hidden (unobservable) states**.

#### **2. Key Concepts**

- **Markov Property**: The future state depends only on the present state, not past states.
- **Hidden States**: The actual system states are unknown but influence the observable outputs.
- **Observations**: The data we see, which depends on the hidden states.
- **Probabilistic Transitions**: Movement between hidden states follows a probability distribution.

![[Pasted image 20250226124645.png]]

#### **4. Three Main Problems in HMM**

1. **Evaluation (Forward Algorithm)**: Compute the probability of an observed sequence.
2. **Decoding (Viterbi Algorithm)**: Find the most likely hidden state sequence for a given observation sequence.
3. **Learning (Baum-Welch Algorithm)**: Adjust model parameters (π,A,B\pi, A, B) to best fit observed data.

#### **5. Applications of HMM**

- **Speech Recognition**: Models phonemes as hidden states.
- **Part-of-Speech Tagging**: Assigns word categories in NLP.
- **Bioinformatics**: DNA sequence alignment and gene prediction.
- **Anomaly Detection**: Fraud detection, system monitoring.

#### **6. Example Scenario**

Imagine trying to predict **weather (hidden states: Sunny, Rainy, Cloudy)** based on **someone’s behavior (observations: Carrying an umbrella, Wearing sunglasses, Staying indoors)**. The HMM models how likely different behaviors are for each weather condition.


---


# 5. Bayesian Network [[Bayesian Network Hinglish]]

#### **1. Definition**

A **Bayesian Network (BN)** is a **probabilistic graphical model** that represents a set of variables and their conditional dependencies using a **Directed Acyclic Graph (DAG)**. It is based on **Bayes’ Theorem** and is used for reasoning under uncertainty.

#### **2. Key Components**

A Bayesian Network consists of:

1. **Nodes** → Represent **random variables** (can be observable, hidden, or unknown).
2. **Directed Edges** → Represent **conditional dependencies** between variables.
3. **Conditional Probability Tables (CPTs)** → Define how a node depends on its parent nodes.

#### **3. Conditional Independence**

- If two nodes are not connected directly, they are **conditionally independent** given their parents.
- Example: If **A → B → C**, then **C is independent of A given B**.

#### **4. Bayes’ Theorem in Bayesian Networks**

P(A∣B)=P(B∣A)P(A)P(B)P(A | B) = \frac{P(B | A) P(A)}{P(B)}

The network factorizes the **joint probability distribution (JPD)** into a product of conditional probabilities:

P(X1,X2,...,Xn)=∏i=1nP(Xi∣Parents(Xi))P(X_1, X_2, ..., X_n) = \prod_{i=1}^{n} P(X_i | Parents(X_i))

#### **5. Example: Disease Diagnosis**

Imagine a Bayesian Network for diagnosing a disease:

- **Flu** → causes **Fever** and **Cough**.
- **Fever** can also be caused by **COVID**.

This can be modeled as:

- P(Flu)P(\text{Flu}) and P(COVID)P(\text{COVID}) (prior probabilities).
- P(Fever∣Flu)P(\text{Fever} | \text{Flu}) and P(Fever∣COVID)P(\text{Fever} | \text{COVID}) (conditional probabilities).
- P(Cough∣Flu)P(\text{Cough} | \text{Flu}).

Given symptoms, we can compute the probability of having Flu or COVID using **inference**.

#### **6. Inference in Bayesian Networks**

- **Exact Inference**: Variable Elimination, Junction Tree Algorithm.
- **Approximate Inference**: Monte Carlo Sampling, Markov Chain Monte Carlo (MCMC).

#### **7. Applications**

- **Medical Diagnosis**: Predict diseases based on symptoms.
- **Fraud Detection**: Identify suspicious transactions.
- **Autonomous Systems**: Decision-making in robotics.
- **Natural Language Processing (NLP)**: Speech recognition, machine translation.

#### **8. Difference Between Bayesian Network & Hidden Markov Model (HMM)**

|Feature|Bayesian Network (BN)|Hidden Markov Model (HMM)|
|---|---|---|
|**Structure**|Directed Acyclic Graph (DAG)|Sequential Model (Markov Chain)|
|**State Representation**|Can represent **both observed and hidden variables**|Only **hidden states** are modeled|
|**Time Dependency**|Not necessarily temporal|Specifically models sequential data|
|**Probabilities**|Uses **Conditional Probability Tables (CPTs)**|Uses **Transition and Emission Matrices**|

Bayesian Networks are **more general** and can represent **complex causal relationships**, while HMMs are **specifically used for sequential data**.

---



