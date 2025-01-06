### کد با کامنت‌ها

در اینجا کد آپلودشده با توضیحات و کامنت‌های فارسی برای هر بخش ارائه شده است:

```python
import nltk
# دانلود داده‌های مورد نیاز برای توکن‌سازی
nltk.download('punkt')

from nltk.tokenize import word_tokenize
import string

# خواندن فایل Vocabulary.txt و ذخیره کردن کلمات در یک مجموعه (Set)
with open('/content/Vocabulary.txt', 'r', encoding='utf-8') as f:
    vocabulary = set(word.strip() for word in f.readlines())

# تابع محاسبه فاصله Damerau-Levenshtein برای تصحیح کلمات
def damerau_levenshtein_distance(s1, s2):
    # ایجاد ماتریس DP برای ذخیره نتایج محاسبات
    dp = [[0] * (len(s2) + 1) for _ in range(len(s1) + 1)]

    # مقداردهی اولیه ماتریس
    for i in range(len(s1) + 1):
        dp[i][0] = i
    for j in range(len(s2) + 1):
        dp[0][j] = j

    # پر کردن ماتریس با استفاده از عملیات درج، حذف، جایگزینی و جابجایی
    for i in range(1, len(s1) + 1):
        for j in range(1, len(s2) + 1):
            if s1[i - 1] == s2[j - 1]:
                cost = 0
            else:
                cost = 1

            dp[i][j] = min(dp[i - 1][j] + 1,  # حذف
                           dp[i][j - 1] + 1,  # درج
                           dp[i - 1][j - 1] + cost)  # جایگزینی

            # بررسی جابجایی حروف (transposition)
            if i > 1 and j > 1 and s1[i - 1] == s2[j - 2] and s1[i - 2] == s2[j - 1]:
                dp[i][j] = min(dp[i][j], dp[i - 2][j - 2] + cost)

    return dp[len(s1)][len(s2)]

# تابع پیشنهاد تصحیحات برای کلمات
def suggest_corrections(word, vocabulary, split_hyphen=True):
    # اگر کلمه شامل خط تیره باشد، آن را به بخش‌های جداگانه تقسیم می‌کنیم
    if split_hyphen and '-' in word:
        parts = word.split('-')
        suggestions = [suggest_corrections(part, vocabulary, split_hyphen=False) for part in parts]
        return '-'.join(suggestions)
    else:
        # پیدا کردن کلمه صحیح با کمترین فاصله
        min_distance = float('inf')
        best_correction = None
        for correct_word in vocabulary:
            distance = damerau_levenshtein_distance(word, correct_word)
            if distance < min_distance:
                min_distance = distance
                best_correction = correct_word
        return best_correction

# جمله‌ای که قرار است پردازش شود
sentence = "Multipmodal usion si a ore proble fofr mpltimodal seuntiment aanlysis."
# توکن‌سازی جمله به کلمات
words = word_tokenize(sentence)

# بررسی هر کلمه در جمله
for word in words:
    # نادیده گرفتن علائم نگارشی
    if word.lower() not in string.punctuation:
        # اگر کلمه در واژگان موجود نباشد، پیشنهاد تصحیح ارائه می‌شود
        if word.lower() not in vocabulary:
            correction = suggest_corrections(word.lower(), vocabulary)
            print(f"Suggestion for '{word}': {correction}")
```

---

### فایل README

در ادامه، فایل README برای این کد آماده شده است:

---

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




If you have any questions or encounter issues, feel free to ask for help. 😊