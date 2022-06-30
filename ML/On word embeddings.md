# On word embeddings

### Part 1

- history of word embeddings
- Word embedding models
  - A note on language modelling
  - Classic neural language model
  - C&W model
  - Word2Vec
    - CBOW
    - Skip-gram

### Part 2: Approximating the Softmax
- Softmax-based Approaches
  - Hierarchical Softmax
  - Differentiated Softmax
  - CNN-Softmax
- Sampling-based Approaches
  - Importance Sampling
  - Adaptive Importance Sampling
  - Target Sampling
  - Noise Contrastive Estimation
  - Negative Sampling
  - Self-Normalisation
  - Infrequent Normalisation
  - Other Approaches

![image](https://user-images.githubusercontent.com/15355357/176792878-3092992e-b3df-4db2-8eee-8453511e8de0.png)

- Which Approach to Choose?


### Part 3: The secret ingredients of word2vec
- GloVe
- Word embeddings vs. distributional semantic models
- Models
- Hyperparameters
  - Pre-processing
    - Dynamic context window
    - Subsampling frequent words
    - Deleting rare words
  - Association metric
    - Shifted PMI
    - Context distribution smoothing
  - Post-processing
    - Adding context vectors
    - Eigenvalue weighting
    - Vector normalisation
