# Persian Text Processing with Hazm

This project is designed to preprocess Persian text using the **Hazm** library. It includes multiple steps such as normalization, sentence and word tokenization, punctuation removal, stopword removal, emoji removal, and lemmatization. The processed text is saved in a new file for further use.

---

## **Features**
- Persian text normalization
- Sentence tokenization
- Word tokenization
- Punctuation removal
- Stopword removal
- Emoji removal
- Lemmatization (root extraction of words)
- Saving the processed text to a file

---

## **Requirements**
To run this project, you need the following:
- Python 3.x
- Hazm library
- A Persian text file as input

---

## **Installation**
1. Install Python 3.x if it's not already installed.
2. Install the required library:
   ```bash
   pip install hazm
   ```

---

## **Usage**
1. Place your Persian text file in the same directory as the script and name it `hp_fa.txt` (or update the `file_path` variable in the script with the correct file name and path).
2. Run the script:
   ```bash
   python nlp_ex1_1.py
   ```
3. After execution, the processed text will be saved in a file named `output.txt` in the same directory.

---

## **Steps in the Script**

### 1. **Normalization**
The script uses Hazm's `Normalizer` to normalize the Persian text. This includes:
- Replacing Arabic characters with their Persian equivalents (e.g., "ي" → "ی").
- Removing extra spaces and unnecessary characters.

### 2. **Sentence Tokenization**
The text is split into individual sentences using Hazm's `sent_tokenize`.

### 3. **Word Tokenization**
Each sentence is further split into words using Hazm's `word_tokenize`.

### 4. **Punctuation Removal**
A custom function `remove_punctuation` removes all non-Persian characters, punctuation marks, and symbols.

### 5. **Stopword Removal**
Common Persian stopwords (e.g., "و", "در", "به") are removed using Hazm's `stopwords_list`.

### 6. **Emoji Removal**
A custom function `remove_emojis` removes all emojis and special symbols from the text.

### 7. **Lemmatization**
Hazm's `Lemmatizer` is used to extract the root form of each word, which is useful for many NLP tasks.

### 8. **Saving the Output**
The processed text is saved line-by-line in a file named `output.txt`.

---

## **Input and Output**
- **Input:** A Persian text file (e.g., `hp_fa.txt`).
- **Output:** A processed text file (`output.txt`) with normalized, tokenized, and cleaned text.


ه نیاز به تغییر دارد، اطلاع دهید تا README به‌روزرسانی شود. 😊