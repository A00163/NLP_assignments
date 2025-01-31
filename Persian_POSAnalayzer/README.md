# Persian POS Tagging and Noun Analysis

This project is designed for processing Persian text data using the **Hazm** library. It performs POS (Part-of-Speech) tagging on a dataset of comments, counts the occurrences of each POS tag, and identifies the top 15 most frequent nouns.

## Features

1. **POS Tagging**: 
   - Tags words in Persian comments using a pre-trained POS tagger.
   
2. **POS Tag Counting**:
   - Counts the frequency of each POS tag across all comments.
   
3. **Noun Extraction**:
   - Extracts and lists the 15 most repeated nouns in the dataset.

4. **Data Export**:
   - Saves the tagged data into a new CSV file for further analysis.

## Requirements

Before running the code, ensure the following dependencies are installed:

- Python 3.x
- [Hazm](https://github.com/sobhe/hazm)
- pandas

You can install Hazm using pip:

```bash
pip install hazm
