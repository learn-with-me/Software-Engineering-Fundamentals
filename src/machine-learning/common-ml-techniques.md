# Common ML Techniques

* **Data Preprocessing** - preparing the data for machine learning models. 
    * This includes cleaning the data, handling missing values, encoding categorical variables, scaling the data, etc.
    * Data preprocessing is an essential step in the machine learning pipeline and is used with all types of machine learning algorithms. 
    * A crucial step before applying any machine learning algorithm, be it regression, classification, or clustering.

* **Dimensionality Reduction** - reducing the number of input variables in a dataset.
    * Used with regression, classification, and clustering algorithms to improve their performance, especially when dealing with high-dimensional data
    * Using feature extraction techniques like `Principal Component Analysis (PCA)`, `t-SNE`, `Hashing` (Locality sensitive hashing), etc.

* **Ensemble Methods** - combining predictions from multiple models to improve the performance and accuracy over any individual model.
    * Techniques like `Bagging`, `Boosting`, `Stacking`, etc.
    * Used with regression and classification algorithms.

* **Evaluation Metrics** - used to evaluate the performance of ML models. 
    * They are used with all types of machine learning tasks including regression (e.g., `Mean Squared Error`), classification (e.g., `Accuracy`, `Precision`, `Recall`), and clustering (e.g., `Silhouette Score`).
    * Common metrics include accuracy, precision, recall, `F1 score`, `ROC-AUC`, etc.

* **Overfitting and Underfitting** - common problems in machine learning where the model performs well on the training data but poorly on the test data.
    * `Overfitting` occurs when the model is too complex and captures noise in the training data.
    * `Underfitting` occurs when the model is too simple and fails to capture the underlying patterns in the data.
    * These concepts apply to all types of machine learning models including regression, classification, and clustering.

* **Neural Networks and Deep Learning** - types of ML model, particularly useful for complex tasks like image recognition, natural language processing, etc.
    * These are a set of algorithms, modeled loosely after the human brain.
    * Different types of neural networks like `Convolutional Neural Networks (CNN)`, `Recurrent Neural Networks (RNN)`, etc.
    * Can be used for a wide range of tasks, including regression, classification, and clustering.

### Neural Networks vs Deep Learning

NN consists of interconnected layers of nodes, or "neurons", and each connection between nodes has a weight that is adjusted during training. Neural networks can learn to perform tasks by considering examples, generally without task-specific programming.

Deep learning is a subfield of machine learning that focuses on neural networks with many layers - hence the term "deep". These deep neural networks are capable of learning from large amounts of data and can automatically extract features from the data during training. This is a key advantage of deep learning over traditional machine learning methods, which often require manual feature extraction. Deep learning is particularly effective for complex tasks such as image recognition, speech recognition, and natural language processing.

### LLM

* **Large Language Model (LLM)**: This is a type of AI model used in natural language processing (NLP). These models, such as GPT-3 or GPT-4, are designed to understand and generate human-like text. They are trained on a large corpus of text data and can generate coherent and contextually relevant sentences. They are used in a variety of applications including translation, question answering, and text generation.  

* **Latent Linear Model (LLM)**: This is a type of statistical model used in machine learning for data analysis. In a latent linear model, the observed data is assumed to be a linear function of some latent (unobserved) variables, plus some noise. These models are often used in dimensionality reduction techniques, such as Principal Component Analysis (PCA), where the goal is to represent high-dimensional data in a lower-dimensional space.
