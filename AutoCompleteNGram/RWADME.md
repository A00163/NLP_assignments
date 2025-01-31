# AutoComplete Model using N-Grams (Unigram, Bigram, Trigram)

This project implements a language model using n-grams (Unigrams, Bigrams, and Trigrams) for Persian text processing. It is designed to process Persian text, tokenize it into words, remove stopwords, normalize the words, and build language models based on n-grams for auto-completion and text analysis.

The model employs **Laplace smoothing** for unigrams and **Good-Turing smoothing** for bigrams and trigrams to estimate probabilities and calculate perplexity, which helps evaluate the quality of the model. The goal of this project is to build an efficient and accurate auto-completion system for Persian text.

## Table of Contents
- [Installation](#installation)
- [Requirements](#requirements)
- [Usage](#usage)
- [How the Code Works](#how-the-code-works)
- [Output](#output)
- [Acknowledgements](#Acknowledgements)

## Installation

Before running the script, you need to install the required dependencies. You can install them using pip:

```bash
!pip install hazm pandas nltk
```

## Requirements

1. **Python 3.x** (preferably Python 3.6 or higher)
2. **Hazm** - A Python library for Persian NLP tasks such as tokenization, stemming, and stopword removal.
3. **Pandas** - Used to handle CSV data efficiently.
4. **NLTK** - A toolkit for handling n-grams, smoothing techniques, and probability distributions.

## Usage

1. Ensure you have a CSV file (`digikala_comment.csv`) containing Persian comments, with a column labeled `comment` containing the text data.
2. Upload the CSV file to your Google Colab environment or adjust the file path as needed.
3. Run the script to preprocess the text, generate n-grams, and build language models.
4. The script will generate probabilities for n-grams, calculate perplexity, and suggest auto-completions based on the trained models.


## How the Code Works

### 1. **Data Preprocessing**
The script starts by reading the comments from the CSV file and joining them into a single string. It then performs the following preprocessing steps:

- Tokenizing the text into sentences using Hazm's `sent_tokenize`.
- Removing punctuation and stopwords.
- Normalizing the words to standardize them (e.g., normalizing Persian characters like "ک" to "ک").
- Tokenizing each sentence into words, removing stopwords, and storing the cleaned words in a list.

### 2. **N-Gram Model Generation**
The code generates three different n-gram models:
- **Unigrams**: Single words.
- **Bigrams**: Pairs of consecutive words.
- **Trigrams**: Triples of consecutive words.

Each sentence is processed to generate these n-grams and their frequencies are counted.

### 3. **Probability Estimation with Smoothing**
- **Unigrams**: Laplace smoothing is applied to estimate the probability of each word.
- **Bigrams and Trigrams**: Good-Turing smoothing is used to estimate the probabilities for sequences of two and three words.

### 4. **Perplexity Calculation**
The perplexity of each model (unigram, bigram, trigram) is calculated for a set of test sentences. Perplexity is a measure of how well the model predicts a sample, with lower perplexity indicating a better model.

### 5. **Auto-Completion**
The auto-completion function generates word suggestions for a given input sentence based on the trained n-gram models. It uses the probabilities of the n-grams to suggest the most likely next word(s) in the sentence. It uses the following approach:
- **Unigrams**: Suggests the most probable word based on frequency.
- **Bigrams and Trigrams**: Takes the previous word(s) as context and suggests the next word(s) based on the model.

## Output

After running the script, the following outputs will be generated:

- **Top 8 N-Grams**: The script will display the most frequent unigrams, bigrams, and trigrams along with their frequencies.
- **Probabilities**: The probabilities of unigrams, bigrams, and trigrams will be displayed using smoothing techniques.
- **Perplexity**: The perplexity of the model will be calculated for some sample sentences, and the script will output the perplexity for each model (unigram, bigram, trigram).
- **Auto-Completion Suggestions**: The script will generate a list of suggested words to complete input sentences, based on unigram, bigram, and trigram models.

Example output for perplexity calculation:

```bash
Perplexity for 'این لپ تاپ سخت افزار خیلی قوی داره و از پس هرکاری به راحتی بر میاد':
  Unigram: 20.47
  Bigram: 15.32
  Trigram: 12.45
```




## Acknowledgements

- The **Hazm** library is used for Persian language processing tasks like tokenization, stemming, and stopword removal.
- The **NLTK** library is used for n-gram generation, frequency distribution, and probability estimation.
```
