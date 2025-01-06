# Spell Checker with Damerau-Levenshtein Distance

This Python script is designed to process a sentence, identify misspelled words, and suggest corrections based on a predefined vocabulary file. It uses the Damerau-Levenshtein distance algorithm to find the closest match for each word.

---

## Features

- **Custom Vocabulary**: Reads a list of correct words from a file (`Vocabulary.txt`).
- **Error Detection**: Identifies words in a sentence that are not in the vocabulary.
- **Error Correction**: Suggests corrections for misspelled words using Damerau-Levenshtein distance.
- **Handles Hyphenated Words**: Supports splitting and correcting hyphenated words.

---

## Requirements

### Python Version
- Python 3.6 or higher

### Required Libraries
Before running the script, ensure the following libraries are installed:
- `nltk`

You can install them using pip:
```bash
pip install nltk
```

---

## Usage

### 1. Prepare the Vocabulary File
Create a file named `Vocabulary.txt` and add a list of valid words, one word per line. For example:
```
multimodal
fusion
is
a
core
problem
for
sentiment
analysis
```

### 2. Write Your Sentence
Modify the `sentence` variable in the script to include the text you want to process. For example:
```python
sentence = "Multipmodal usion si a ore proble fofr mpltimodal seuntiment aanlysis."
```

### 3. Run the Script
Run the script using Python:
```bash
python nlp_ex1_3.py
```

### 4. Output
The script will print suggestions for misspelled words. For example:
```
Suggestion for 'Multipmodal': multimodal
Suggestion for 'usion': fusion
Suggestion for 'si': is
Suggestion for 'ore': core
Suggestion for 'proble': problem
Suggestion for 'fofr': for
Suggestion for 'mpltimodal': multimodal
Suggestion for 'seuntiment': sentiment
Suggestion for 'aanlysis': analysis
```

---

## Code Structure

### Main Steps:
1. **Vocabulary Loading**:
   - Reads the vocabulary from `Vocabulary.txt` and stores it in a set for fast lookup.
2. **Sentence Tokenization**:
   - Tokenizes the input sentence into individual words using `nltk.word_tokenize`.
3. **Error Detection and Correction**:
   - For each word not found in the vocabulary, calculates the Damerau-Levenshtein distance to suggest the closest match.
4. **Handles Hyphenated Words**:
   - Splits words containing hyphens and processes each part separately.
