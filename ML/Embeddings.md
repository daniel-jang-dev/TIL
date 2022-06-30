# Embeddings

### Dealing with Text
- Input = ["the", "quick", "brown", "fox", "jumps", "over", "the", "lazy", "dog"]
- Thus:
  - x<sub>1</sub> = "the"
  - x<sub>2</sub> = "quick"
  - ...
- We cannot do something like:
$$ h_t = {\sigma} ({W_{xh}}^T x_t + {W_{hh}}^T h_{t-1} + b_h)$$
- Because $x(t)'s$ are not numerical!

### One-Hot Encoding?
- Create an array of size equal to the number of words in the English language (call that "V")
- vector = [0, 0, 0, 0, 0, ...., 0]
- Map each word to an index (where it becomes 1)
  - "a" → [1,0,0,...,0] (index 1)
  - "aa" → [0, 1, 0, ...,O] (index 2)
  - ...
  - "activation" → [0, 0, 0, ..., 1, ..., 0] (index 100)
  - ...
  - "zoo" → [0, 0, 0, ..., 1] (index 1 million)
- If we have a sequence of T words, and each word gets a one-hot encoded vector of size V, then one sentence becomes a Tx V matrix
- Same generic shape as a TxD matrix (as you saw previously)
- E.g. “I like cats'
- Might become: [[0, 0, 0, 1], [0, 1, 0, 0], [1, 0, 0, 0]]
- (If we had a 4-word vocabulary)

### Problem!
- Some English-language datasets have ~1 million possible tokens / words
- This means V (or equivalently, D) is 1 million
- Not only is the input large, but the input-hidden weight matrix will also be large!
- In actuality, the English dictionary has –200,000 words, but this is still a very large number

### Another problem!
- Recall: we want our input features to have some structure
- "Machine learning is nothing but a geometry problem"
- This rule **relies** on the fact that there's some geometrical structure in the data - that data vectors in the same class (e.g. spam vs. not spam) are _probably_ near each other

### Problem with one-hot encoding
- Take any two one-hot encoded vectors, e.g. [1, 0, 0] vs. [0, 1, 0]
- The Euclidean distance is $\sqrt{1^2 + 1^2} = \sqrt{2}$
- All words therefore are an equal distance apart!
- The distance between "cat" and "feline" is $\sqrt{2}$
- The distance between "cat" and "airplane" is also $\sqrt{2}$
- Useless!

### A better solution: Embeddings
- Assign each word to a D-dimensional vector (not one-hot encoded)
- How are these vectors "found"? We will see shortly!
![image](https://user-images.githubusercontent.com/15355357/176754778-da7cc1ae-bd30-4774-a7a3-6e803a342dac.png)

### What's the pattern?
- If the index set to 1 is located at position 1, we get the first row
- If the index set to 1 is located at position 2, we get the second row
- If the index set to 1 is located at position 3, we get the third row
![image](https://user-images.githubusercontent.com/15355357/176755116-51047a41-fa76-460a-a493-95bf8278c3bd.png)

### Why is it more efficient?
- Old way takes 2 steps: 
  - Create a vector of size V containing all zeros, set the k'th entry to 1
  - Multiply the one hot vector by the weight matrix
- New way takes 1 step: 
  - Index the weight matrix (W[k])
- Indexing an array is O(1) - constant time
- Multiplying a length V vector by a V x D matrix is O(VD)

### Tensorflow Embedding
- This is exactly what the Embedding layer does!
- STEP #1: Convert words into integers
  - ["1", "Like", "Cats"] → [50, 25, 3] 
- STEP #2: Use integers to index the word embedding matrix to get word vectors for each word
  - [50, 25, 3] → [[0.3, -0.5], [1.2, -0.7], [-2.1, 0.9]] 
  - T-length array → T x D matrix

### How are the weights found?
- We know intuitively that the word vectors must have some useful structure
- Luckily, it's the same story as with convolutional filters
- These weights are found automatically with gradient descent when you call `model.fit()`

### Pre-trained word vectors
- Sometimes, we use _pre-trained_ word vectors (trained using some other algorithm)
- We freeze (fix) the embedding layer's weights, so only the _other_ layers are trained when we call `model.fit()`

![image](https://user-images.githubusercontent.com/15355357/176756275-c3ec9da0-085e-4035-9d18-4afde0b4b1cf.png)

### Summary
- It's not possible to multiply a word by a weight matrix - there is no concept of multiplying words
- We must turn words into some kind of numerical representation first
- One-hot encoding is a fine first guess
  - Too much space (there could be up to 1 million tokens)
  - Not geometrically useful ("cat" is just as close to "feline" as it is to "airplane")
  - We need to make use of "machine learning is nothing but a geometry problem"
- Better: convert words to unique integers
- Use those integers to _index_ a weight matrix (the _embedding matrix_)
- Much faster than matrix multiplication
- Each input sentence thus becomes a T x D sequence which we know an RNN can accept
- The embedding is trained like any other layer - we just need to call `model.fit()`
![image](https://user-images.githubusercontent.com/15355357/176756793-ad4e1246-ad2d-4cd7-8528-a1a43127abd3.png)

