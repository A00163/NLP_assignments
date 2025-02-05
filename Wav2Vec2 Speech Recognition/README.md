

```markdown
# Overview

This repository provides a comprehensive workflow for building and training a Persian speech recognition model using the **Wav2Vec2** framework. It processes the **Common Voice Dataset** for the Persian language (`fa`) and leverages **HuggingFace Transformers** for model training.

---

## Table of Contents

1. [Installation](#installation)
2. [Dataset](#dataset)
3. [Data Preprocessing](#data-preprocessing)
4. [Model and Tokenizer](#model-and-tokenizer)
5. [Training](#training)
6. [Evaluation](#evaluation)
7. [Acknowledgements](#acknowledgements)

---

## Installation

### Required Libraries

Install the necessary libraries using `pip`:

```bash
pip install datasets
pip install huggingface_hub
pip install hazm
pip install torchaudio librosa transformers
pip install accelerate -U
pip install jiwer
```

---

## Dataset

The code uses the **Mozilla Common Voice 6.1 Dataset** for Persian (`fa`). The dataset is directly loaded from HuggingFace Datasets.

- **Training Data**: Audio files with durations between **4 and 6 seconds**.
- **Testing Data**: Audio files with durations between **0 and 15 seconds**.

The dataset is preprocessed by removing unnecessary columns such as `age`, `gender`, and `client_id`.

---

## Data Preprocessing

### 1. **Normalization**:
- Replace non-standard Persian characters (e.g., `ك` → `ک`).
- Remove unwanted symbols and punctuation marks.

### 2. **Vocabulary Creation**:
- A unique character set from the dataset is used to create a vocabulary (`vocab.json`).
- Special tokens like `<s>`, `</s>`, `<unk>`, and `|` are added.

### 3. **Audio Resampling**:
- The audio files are resampled from **48kHz** to **16kHz** for compatibility with the Wav2Vec2 model.

---

## Model and Tokenizer

### 1. **Tokenizer**:
- Created using `Wav2Vec2CTCTokenizer` with the custom vocabulary.
- The tokenizer is saved locally for future use.

### 2. **Feature Extractor**:
- Extracts features from the audio files and normalizes them.

### 3. **Processor**:
- Combines both the tokenizer and feature extractor for preprocessing text and audio data.

### 4. **Model**:
- Uses the pre-trained `facebook/wav2vec2-base` model.
- The feature extractor is frozen during training to focus on fine-tuning the model's classification head.

---

## Training

### Training Configuration:
- **Batch Size**: 6
- **Epochs**: 2
- **Learning Rate**: `1e-4`
- **Evaluation Strategy**: Every 500 steps
- **Weight Decay**: `0.005`

### Data Collation:
A custom data collator is used to dynamically pad audio inputs and labels during training.

### Trainer:
The HuggingFace `Trainer` is used to handle the training process, evaluation, and checkpointing. A custom callback is implemented to save the model at the end of each epoch.

---

## Evaluation

### Metrics:
- **Word Error Rate (WER)**: Computed using the `jiwer` library.
- WER is calculated by comparing model predictions with ground truth labels from the test dataset.

---

## Key Outputs

1. **Vocabulary File**:
   - `vocab.json`: Contains the character-to-index mapping.

2. **Trained Model**:
   - Checkpoints of the fine-tuned Wav2Vec2 model are saved during training.

3. **Metrics**:
   - Word Error Rate (WER) on the test dataset.

4. **Model Parameters**:
   - Total number of trainable and non-trainable parameters.

---

## Acknowledgements

This project leverages:
- **HuggingFace Transformers** for model training and tokenization.
- **Common Voice Dataset** for the speech recognition data.
- **Hazm Library** for Persian text normalization.

For further details, visit:
- [HuggingFace Transformers](https://huggingface.co/docs/transformers/)
- [Common Voice Dataset](https://commonvoice.mozilla.org/)
- [Hazm Library](https://github.com/sobhe/hazm)

---
```