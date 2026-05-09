# NLP Generative Chatbot

Group project for the NLP module — implementing a generative chatbot using Sequence-to-Sequence (seq2seq) models on the WikiQA dataset.

## Models

| # | Model | Architecture |
| --- | --- | --- |
| 1 | Basic Seq2Seq | LSTM encoder–decoder, no attention |
| 2 | Luong Attention Seq2Seq | LSTM encoder–decoder + Luong dot-product attention |

## Dataset — WikiQA

**WikiQA Corpus** — question–answer sentence pairs sourced from Wikipedia (Microsoft Research, 2015).

Download the dataset manually from the Microsoft Research page and place the extracted files in `data/raw/`:

[https://www.microsoft.com/en-us/download/details.aspx?id=52419](https://www.microsoft.com/en-us/download/details.aspx?id=52419)

## Project structure

```text
.
├── data/
│   ├── raw/        # Downloaded dataset cache (git-ignored)
│   └── processed/  # Any processed/encoded data (git-ignored)
├── notebooks/      # Jupyter notebooks go here
├── results/        # Outputs, plots, checkpoints (git-ignored)
├── pyproject.toml
└── README.md
```

## Environment setup

This project uses [uv](https://github.com/astral-sh/uv) for dependency management.

```bash
# Clone the repo and cd into it
git clone <repo-url>
cd nlp-generative-chatbot

# Create the virtual environment and install all dependencies
uv sync
```

## Running notebooks

```bash
uv run jupyter lab
```

## Code quality

Please keep the code clean and well-documented. Use `ruff` for linting and formatting:

```bash
uv run ruff check
uv run ruff format
```
