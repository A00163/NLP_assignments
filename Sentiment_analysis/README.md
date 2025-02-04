

### **Overview**
This project focuses on building a **sentiment analysis model** to classify tweets as **positive** or **negative**. The workflow involves data preprocessing, feature engineering, and training deep learning models such as **RNN** and **LSTM** using **Google News Word2Vec embeddings** for text representation.

The dataset used is **Sentiment140**, which contains 1.6 million tweets labeled as either positive (1) or negative (0).

---

### **Workflow Steps**

#### 1. **Dataset Loading and Visualization**
   - The dataset (`sentiment140.csv`) is loaded into a pandas DataFrame.
   - The distribution of sentiments is visualized using `Seaborn` to identify class imbalance.

#### 2. **Data Preprocessing**
   - **Label Conversion**: Replace sentiment label `4` with `1` to ensure binary classification.
   - **Text Cleaning**: Replace:
     - URLs with `URL`
     - Mentions with `MENTION`
     - Hashtags with `HASHTAG`
   - **Punctuation Removal**: Remove all punctuation marks from tweets.
   - **Tokenization**: Split each tweet into individual words using `nltk`.
   - **Lemmatization**: Reduce words to their base forms for consistency (e.g., "running" → "run").

#### 3. **Dataset Analysis**
   - Visualize the length distribution of tweets to determine an optimal sequence length for padding.
   - Use cumulative distribution to decide the 95th percentile as the maximum sequence length.

#### 4. **Word Embedding**
   - Use **Google News Word2Vec** pre-trained embeddings for vectorization.
   - Map each token to its corresponding 300-dimensional embedding vector. For unknown words, random embeddings are assigned.

#### 5. **Data Preparation**
   - Split the dataset into training (80%), validation (10%), and test (10%) subsets.
   - Tokenize tweets and convert them into padded sequences of the same length for model input.

#### 6. **Model Training**
   - Two models are implemented:
     1. **Simple RNN**:
        - Embedding Layer (pre-trained Word2Vec)
        - Simple RNN Layer (64 units)
        - Dropout (0.5)
        - Dense Output Layer (with L2 regularization)
     2. **LSTM**:
        - Embedding Layer (pre-trained Word2Vec)
        - LSTM Layer (128 units)
        - Dense Output Layer with Sigmoid Activation

   - Compile models with:
     - Optimizer: `Adam`
     - Loss: Binary Crossentropy
     - Metric: Accuracy

#### 7. **Evaluation**
   - Predict sentiments on the test set.
   - Generate a classification report including metrics such as **precision**, **recall**, **F1-score**, and **accuracy**.

---

### **Requirements**

#### **Python Libraries**
- **Data Handling**: pandas, numpy
- **Text Processing**: nltk, re, string
- **Visualization**: seaborn, matplotlib
- **Machine Learning**: sklearn
- **Deep Learning**: tensorflow, keras
- **Pre-trained Word Embeddings**: gensim

#### **Installation**
```bash
pip install pandas numpy nltk seaborn matplotlib sklearn tensorflow gensim
```

---

### **Usage**

1. Clone the repository or download the code.
2. Ensure all required libraries are installed.
3. Place the dataset `sentiment140.csv` in the working directory.
4. Run the notebook `Sentiment_analysis.ipynb` in Google Colab or Jupyter Notebook.

---


