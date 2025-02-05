```markdown
# overview

This repository contains a complete workflow for building and training a speech recognition model using the Wav2Vec2 framework. It processes the **Common Voice Dataset** in Persian (`fa`) and uses **HuggingFace Transformers** for model training.

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

The code uses the **Mozilla Common Voice 6.1 Dataset** for Persian (`fa`). The dataset is downloaded directly from HuggingFace Datasets.

- **Training Data**: Filtered audio files with durations between **4 and 6 seconds**.
- **Testing Data**: Filtered audio files with durations between **0 and 15 seconds**.

The dataset is preprocessed to remove unnecessary columns such as `age`, `gender`, and `client_id`.

---

## Data Preprocessing

1. **Normalization**:
   - Replace non-standard Persian characters (e.g., `ك` → `ک`).
   - Remove unwanted symbols and punctuation marks.

2. **Vocabulary Creation**:
   - Unique characters in the dataset are used to create a vocabulary (`vocab.json`).
   - Special tokens like `<s>`, `</s>`, `<unk>`, and `|` are added.

3. **Audio Resampling**:
   - Audio files are resampled from **48kHz** to **16kHz** for compatibility with Wav2Vec2.

---

## Model and Tokenizer

1. **Tokenizer**:
   - Created using `Wav2Vec2CTCTokenizer` with the custom vocabulary.
   - Saved locally for future use.

2. **Feature Extractor**:
   - Extracts features from the audio and normalizes them.

3. **Processor**:
   - Combines the tokenizer and feature extractor to preprocess both text and audio.

4. **Model**:
   - Uses the pre-trained `facebook/wav2vec2-base` model.
   - The feature extractor is frozen during training to focus on fine-tuning the classification head.

---

## Training

### Training Configuration
- **Batch Size**: 6
- **Epochs**: 2
- **Learning Rate**: `1e-4`
- **Evaluation Strategy**: Every 500 steps
- **Weight Decay**: `0.005`

### Data Collation
A custom `DataCollator` is used to pad audio inputs and labels dynamically during training.

### Trainer
The HuggingFace `Trainer` is used to handle training, evaluation, and checkpointing. A custom callback is implemented to save the model at the end of each epoch.

---

## Evaluation

### Metrics
- **Word Error Rate (WER)**: Computed using the `jiwer` library.
- WER is calculated based on model predictions and ground truth labels from the test dataset.

---

## Key Outputs

1. **Vocabulary File**:
   - `vocab.json`: Contains the character-to-index mapping.

2. **Trained Model**:
   - Saved checkpoints for the fine-tuned Wav2Vec2 model.
   - Checkpoints are saved after each epoch.

3. **Metrics**:
   - Word Error Rate (WER) on the test set.

4. **Parameters**:
   - Total trainable and non-trainable parameters are printed.

---

## Acknowledgements

This project utilizes:
- **HuggingFace Transformers** for model training and tokenization.
- **Common Voice Dataset** for speech data.
- **Hazm Library** for text normalization.

For more details, visit:
- [HuggingFace Transformers](https://huggingface.co/docs/transformers/)
- [Common Voice Dataset](https://commonvoice.mozilla.org/)
- [Hazm Library](https://github.com/sobhe/hazm)

---
```