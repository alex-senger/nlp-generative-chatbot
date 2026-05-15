# NLP Generative Chatbot

Group project for the NLP module — implementing a generative chatbot using a Sequence-to-Sequence (seq2seq) LSTM model trained on the WikiQA dataset.

## Overview

Two independent pipelines are implemented, each with its own preprocessing and model notebook:

| Pipeline | Training data | Notebooks |
| --- | --- | --- |
| **correct-answers-only** | Label=1 rows only (728 Q&A pairs) | `notebooks/correct-answers-only/` |
| **full-dataset** | All rows, Label=0 and Label=1 (16,206 Q&A pairs) | `notebooks/full-dataset/` |

Both pipelines use the same architecture: a single-layer LSTM encoder–decoder with no attention.

## Dataset — WikiQA

**WikiQA Corpus** — question–answer sentence pairs sourced from Wikipedia (Microsoft Research, 2015).

**Local:** download from the Microsoft Research page and place the extracted files in `data/raw/`:

[https://www.microsoft.com/en-us/download/details.aspx?id=52419](https://www.microsoft.com/en-us/download/details.aspx?id=52419)

**Google Colab:** the preprocessing notebooks detect the Colab environment automatically and download the dataset from HuggingFace — no manual step needed.

## Project structure

```text
.
├── data/
│   ├── raw/             # Downloaded dataset files (git-ignored)
│   ├── processed/       # Encoded correct-answers-only splits (git-ignored)
│   └── processed_full/  # Encoded full-dataset splits (git-ignored)
├── notebooks/
│   ├── correct-answers-only/
│   │   ├── 01_preprocessing.ipynb
│   │   └── 02_seq2seq_basic.ipynb
│   └── full-dataset/
│       ├── 01_preprocessing.ipynb
│       └── 02_seq2seq_basic.ipynb
├── results/             # Checkpoints and plots (git-ignored)
├── pyproject.toml
└── README.md
```

## Running locally

This project uses [uv](https://github.com/astral-sh/uv) for dependency management.

```bash
# Clone the repo and cd into it
git clone <repo-url>
cd nlp-generative-chatbot

# Create the virtual environment and install all dependencies
uv sync

# Launch Jupyter
uv run jupyter lab
```

Run notebooks in order within each pipeline: `01_preprocessing.ipynb` first, then `02_seq2seq_basic.ipynb`.

## Running in Google Colab

Each notebook detects the Colab environment automatically. Open each notebook in Colab, select a GPU runtime (Runtime > Change runtime type > T4 GPU), and run cells top-to-bottom. Run `01_preprocessing.ipynb` before `02_seq2seq_basic.ipynb` in the same session so the processed files are available.
