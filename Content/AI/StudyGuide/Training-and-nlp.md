## Study Guide

#### Topics
1. Training
2. NLP concepts

#### Questions

1. What is backpropagation, and how is it used in training neural networks?
2. Can you explain the role of the chain rule in backpropagation?
3. How does backpropagation differ in RNNs compared to feedforward neural networks?
4. What are autoregressive models, and how are they used in NLP?
5. How does the GPT series of models use autoregressive principles?
6. Can you compare autoregressive models with autoencoder models in terms of their applications in NLP?
7. What is the significance of context in word embeddings, and how do models like BERT and GPT handle context differently?
8. How do sequence-to-sequence models work, and what are their applications in NLP?
9. Explain the concept of attention mechanisms and their evolution in NLP models.
10. What are common loss functions used in NLP tasks, and how are they chosen?
11. Discuss gradient descent and its variants used in neural network training.
12. Explain the concept of overfitting and underfitting in machine learning.
13. What is the role of dropout and regularization in neural networks?
14. What role does Named Entity Recognition (NER) play in NLP, and how do modern NLP models approach NER tasks?

### NLP
1. What is backpropagation, and how is it used in training neural networks?  
**Expected Answer**: Backpropagation is a method used to calculate the gradient of the loss function in neural networks. It involves a forward pass where the input data is passed through the network to get the output, and a backward pass where the gradient of the loss function is computed backward through the network. This information is then used to update the weights of the network, optimizing the model during training.

1. Can you explain the role of the chain rule in backpropagation?  
**Expected Answer**: The chain rule is used in backpropagation to compute the derivatives of the loss function with respect to each weight in the network. It allows the gradient of the loss with respect to the output to be propagated back through the layers of the network, computing the partial derivatives at each step.

1. How does backpropagation differ in RNNs compared to feedforward neural networks?  
**Expected Answer**: In RNNs, backpropagation through time (BPTT) is used. BPTT involves unrolling the RNN for the sequence's length and then applying backpropagation. This is different from feedforward networks where backpropagation is straightforward since there are no recurrent connections.

1. What are autoregressive models, and how are they used in NLP?  
**Expected Answer**: Autoregressive models predict future values in a sequence based on previous values. In NLP, they are used for tasks like text generation, where each new word is predicted based on the previously generated words.

1. How does the GPT series of models use autoregressive principles?  
**Expected Answer**: The GPT series of models, being transformer-based, use autoregressive principles to generate text. Each token is predicted based on all the previous tokens, making them powerful for coherent and context-aware text generation.

1. Can you compare autoregressive models with autoencoder models in terms of their applications in NLP?  
**Expected Answer**: Autoregressive models focus on predicting subsequent elements in a sequence, ideal for generative tasks. Autoencoder models, on the other hand, are designed for encoding an input into a lower-dimensional space and then reconstructing the output, used for tasks like denoising or unsupervised learning.

1. What is the significance of context in word embeddings, and how do models like BERT and GPT handle context differently?  
**Expected Answer**: Context is crucial in understanding the meaning of words in language. Models like BERT use bidirectional context, analyzing text from both left and right of a word, while GPT uses unidirectional (left-to-right) context. This contextual understanding helps in more accurate representations of word meanings.

1. How do sequence-to-sequence models work, and what are their applications in NLP?  
**Expected Answer**: Sequence-to-sequence models are used in NLP for tasks where the input and output are sequences, like translation or summarization. They typically consist of an encoder that processes the input sequence and a decoder that generates the output sequence.

1. Explain the concept of attention mechanisms and their evolution in NLP models.  
**Expected Answer**: Attention mechanisms allow models to focus on relevant parts of the input when generating each part of the output. They started with simple forms in models like seq2seq and evolved to more complex and efficient forms in models like Transformers.

1. What are common loss functions used in NLP tasks, and how are they chosen?  
**Expected Answer**: Common loss functions in NLP include cross-entropy loss for classification tasks and sequence generation, and mean squared error for regression tasks. The choice depends on the specific task and the model's output.

1. Discuss gradient descent and its variants used in neural network training.  
**Expected Answer**: Gradient descent is an optimization algorithm used to minimize the loss function in neural networks. Its variants include stochastic gradient descent (SGD), which updates weights using only a subset of data, and adaptive methods like Adam and RMSprop, which adjust the learning rate during training.

1. Explain the concept of overfitting and underfitting in machine learning.  
**Expected Answer**: Overfitting occurs when a model learns the training data too well, including its noise and fluctuations, leading to poor performance on new data. Underfitting happens when a model is too simple to capture the underlying pattern in the data. Both lead to poor generalization.

1. What is the role of dropout and regularization in neural networks?  
**Expected Answer**: Dropout is a technique used to prevent overfitting by randomly setting a subset of activations to zero during training. This helps the network to learn more robust features. Regularization, such as L1 or L2 regularization, penalizes the model for having large weights, which also helps in reducing overfitting by encouraging the model to learn simpler patterns.

1. What role does Named Entity Recognition (NER) play in NLP, and how do modern NLP models approach NER tasks?  
**Expected Answer**: NER is crucial in NLP for identifying and classifying key information in text, like names of people, organizations, locations, etc. Modern NLP models, often transformer-based, use contextual information to accurately identify and classify these entities.
