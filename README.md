# Multimodal Styled Image Captioning System

A multimodal image captioning system that generates captions in different stylistic variations (e.g., funny, romantic, sentimental) using vision-language models. The system fine-tunes BLIP on style-specific datasets to produce captions that go beyond factual descriptions.

## Overview

This project implements a two-phase training pipeline for styled image captioning:

- **Phase 1**: Train on raw/neutral captions to establish baseline image understanding
- **Phase 2**: Fine-tune on styled captions (funny, romantic, positive/negative sentiment) to learn stylistic generation

## Datasets

The system uses the **FMNLP dataset**, which combines:

- **FlickerStyle**: Images with neutral, funny, and romantic captions
- **Senticap**: Images with sentiment-styled captions (positive/negative)

## Project Structure

| File | Description |
|------|-------------|
| `part1.ipynb` | Data preparation, model training, and evaluation pipeline |
| `Part2.ipynb` | Alternative implementation with custom BLIP modifications |

## Requirements

- Python 3.10+
- PyTorch
- Transformers (Hugging Face)
- Datasets (Hugging Face)
- pandas, numpy, PIL
- rouge, nltk (for evaluation metrics)

## Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/ReyhanehAhani/Multimodal-Styled-Image-Captioning-System.git
   cd Multimodal-Styled-Image-Captioning-System
   ```

2. **Install dependencies**
   ```bash
   pip install torch transformers datasets pandas numpy pillow rouge nltk gdown
   ```

3. **Download the dataset**
   - The notebooks use Google Colab with Google Drive
   - Dataset is downloaded via `gdown` (Google Drive ID: `10-P4uCqCp1NMFfI-2O_Y1vjBGcF2ew6c`)
   - Update paths in the notebooks to match your environment

## Usage

The notebooks are designed to run on **Google Colab**:

1. Upload the notebooks to Colab
2. Mount Google Drive and ensure the dataset is available (or download it as shown in the first cells)
3. Run cells sequentially

### Key Steps

1. **Data loading**: Load FlickerStyle and Senticap datasets, split into train/test
2. **Model**: Uses `Salesforce/blip-image-captioning-base` from Hugging Face
3. **Training**: Fine-tune BLIP with style-conditioned prompts (e.g., "a funny picture of", "a romantic picture of")
4. **Evaluation**: BLEU, ROUGE-1, ROUGE-2, ROUGE-L, and METEOR scores

## Model

- **Base model**: [BLIP (Bootstrapping Language-Image Pre-training)](https://huggingface.co/Salesforce/blip-image-captioning-base)
- **Conditioning**: Style is injected via prefix prompts (e.g., "a funny picture of", "a romantic picture of")

## Evaluation Metrics

- **BLEU**: N-gram overlap with reference captions
- **ROUGE**: Recall-oriented metrics (ROUGE-1, ROUGE-2, ROUGE-L)
- **METEOR**: Semantic similarity and stemming

## License

This project is for research and educational purposes.
