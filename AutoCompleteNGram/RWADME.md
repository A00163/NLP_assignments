# AutoComplete Model using N-Grams (Unigram, Bigram, Trigram)

This project implements a language model using n-grams (Unigrams, Bigrams, and Trigrams) for Persian text processing. It is designed to process Persian text, tokenize it into words, remove stopwords, normalize the words, and build language models based on n-grams for auto-completion and text analysis.

The model employs **Laplace smoothing** for unigrams and **Good-Turing smoothing** for bigrams and trigrams to estimate probabilities and calculate perplexity, which helps evaluate the quality of the model. The goal of this project is to build an efficient and accurate auto-completion system for Persian text.

## Table of Contents
- [Installation](#installation)
- [Requirements](#requirements)
- [Usage](#usage)
- [How the Code Works](#how-the-code-works)
- [Output](#output)
- [License](#license)

## Installation

Before running the script, you need to install the required dependencies. You can install them using pip:

```bash
!pip install hazm pandas nltk
