# Word Cloud Generator

This project is a simple Python script that processes a text file, removes unnecessary elements (like numbers, URLs, punctuation, and stopwords), and generates a **Word Cloud** visualization from the processed text.

## Features
- Tokenizes sentences and words using the `nltk` library.
- Removes numbers, URLs, punctuation, and common English stopwords.
- Generates a Word Cloud visualization using the `wordcloud` library.
- Displays the Word Cloud using `matplotlib`.

---

## Requirements

### Python Version
- Python 3.6 or higher

### Required Libraries
Before running the script, make sure the following libraries are installed:
- `nltk`
- `wordcloud`
- `matplotlib`

You can install them using pip:
```bash
pip install nltk wordcloud matplotlib
```

---

## Usage

### 1. Prepare the Text File
Place the text file you want to analyze in the same directory as the script or provide the correct path to it. For example, create a file named `hp_en.txt` with the following sample content:

```text
Harry Potter is a series of seven fantasy novels written by British author J. K. Rowling.
The novels chronicle the lives of a young wizard, Harry Potter, and his friends Hermione Granger and Ron Weasley.
They are students at Hogwarts School of Witchcraft and Wizardry.
The main story arc concerns Harry's struggle against Lord Voldemort, a dark wizard who intends to become immortal.
```

Save this file in the `/content/` directory (or adjust the path in the script).

### 2. Run the Script
Run the script using Python:
```bash
python nlp_ex1_2.py
```

### 3. Output
The script will process the text file and display a **Word Cloud** visualization. The Word Cloud highlights the most frequently occurring words in the text.

---

## Code Structure

### Main Steps:
1. **Text Preprocessing**:
   - Reads the text file.
   - Converts the text to lowercase.
   - Removes numbers, URLs, punctuation, and stopwords.
2. **Word Cloud Generation**:
   - Combines the processed words into a single string.
   - Creates a Word Cloud using the `WordCloud` library.
3. **Visualization**:
   - Displays the Word Cloud using `matplotlib`.


If you have any questions or encounter issues, feel free to ask for help. 😊