# A piece of cake is not always sweet: detecting idiomatic language use
# Multimodal Idiom Sense Disambiguation

## Overview

This repository contains the code for my MSc dissertation project on multimodal idiom sense disambiguation. The project investigates the integration of textual and visual modalities to improve the disambiguation of English multi-word expressions (MWEs) or idioms.

The approach combines:
- **Textual Analysis**: Using DistilBERT for processing textual context and idiom representations.
- **Visual Analysis**: Using Inception v3 for analyzing images associated with idioms.
- **Feature Fusion**: Combining text and image features through a multimodal neural network.

## Project Structure

```
.
├── dataset/                    # Training dataset
│   ├── multimodal_train_json.csv
│   ├── train_json.csv
├── models/                     # Model training and evaluation notebooks
│   ├── featureFusion.ipynb     # Multimodal fusion model combining text and image features
│   ├── inception_v3.ipynb      # Image classification using Inception v3
│   ├── text_BERT.ipynb         # Text classification using DistilBERT
│   └── weights/                # Saved model weights
│       ├── 20210922_final_bert_saved_weights.pth
│       ├── 20210922_final_combined_saved_weights.pth
│       └── 20210922_final_inception_weights.pth
└── preprocessing/              # Data preprocessing scripts
    ├── DatasetImageScraping.ipynb  # Image scraping from Google Images
    ├── imageSenses.csv         # Idiom sense definitions
    └── newTraining.ipynb       # Training data preparation and filtering
```

## Dataset

The dataset consists of:
- **Text Data**: CSV files containing idioms, their contexts, and sense labels (idiomatic vs. literal, and fine-grained senses).
- **Image Data**: Images scraped from Google Images for each idiom, organized by sense categories.

## Models

### Text Model (text_BERT.ipynb)
- Uses DistilBERT for text classification
- Processes idiom contexts and predicts sense labels
- Trained on filtered training data

### Image Model (inception_v3.ipynb)
- Fine-tunes Inception v3 for image classification
- Classifies images associated with different idiom senses

### Fusion Model (featureFusion.ipynb)
- Combines features from text and image models
- Implements a multimodal dataset class and fusion network
- Achieves improved performance through joint learning

## Preprocessing

### Image Scraping (DatasetImageScraping.ipynb)
- Scrapes images from Google Images using Selenium
- Downloads and organizes images by idiom and sense
- Handles rate limiting and duplicate removal

### Data Preparation (newTraining.ipynb)
- Filters training data (removes proper nouns and meta usages)
- Analyzes sense frequencies
- Prepares balanced training sets

### Sense Definitions (imageSenses.csv)
- Contains idiom definitions with frequent senses and fine-grained labels
- Used for data validation and sense mapping

## Requirements

- Python 3.7+
- PyTorch
- Transformers
- Torchvision
- Pandas
- NumPy
- PIL (Pillow)
- Selenium (for image scraping)
- ChromeDriver (for Selenium)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ronan4d97/multimodal-idiom-disambiguation.git
   cd multimodal-idiom-disambiguation
   ```

2. Install dependencies:
   ```bash
   pip install torch torchvision transformers pandas numpy pillow selenium
   ```

3. Download ChromeDriver and place it in the appropriate path (as specified in the scraping notebook).

## Usage

1. **Data Preparation**:
   - Run `preprocessing/DatasetImageScraping.ipynb` to scrape images (requires dataset CSV)
   - Run `preprocessing/newTraining.ipynb` to prepare training data

2. **Model Training**:
   - Train text model: `models/text_BERT.ipynb`
   - Train image model: `models/inception_v3.ipynb`
   - Train fusion model: `models/featureFusion.ipynb`

3. **Evaluation**:
   - Each notebook includes evaluation sections
   - Saved weights are available in `models/weights/`

## Results

The multimodal fusion approach shows improved performance over unimodal baselines. Saved model weights from the final experiments are included for reproducibility.

## License

This project is part of a dissertation submission. Please contact the author for usage permissions.
