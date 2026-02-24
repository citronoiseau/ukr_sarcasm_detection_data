# Cross-Lingual Sarcasm Detection: Ukrainian Sarcasm Dataset

This repository contains the training and evaluation datasets used in the preprint:

**Overcoming the Alignment Tax: Cross-Lingual Sarcasm Detection with Llama 3 in Low-Resource Contexts**  
[Insert arXiv link here]

---

## Overview

This repository provides two Ukrainian-language datasets designed to evaluate cross-lingual sarcasm detection and investigate the “alignment tax” in Large Language Models.

Both datasets are derived from the Irony/Sarcasm subset of the `tweet_eval` benchmark and were sanitized to remove explicit lexical shortcuts (e.g., `#sarcasm`, `#irony`, emojis, and other direct sarcasm markers).

To study the effect of data quality on cross-lingual transfer, we release two versions:

- **Non-Curated Dataset** — automatic machine translations
- **Curated Dataset** — human-verified and filtered translations

---

## Repository Structure

```
├── non-curated/
│   ├── uk_autotranslate_sarcasm_train.csv
│   └── uk_autotranslate_sarcasm_test.csv
└── curated/
    ├── uk_train_100.csv
    ├── uk_train_200.csv
    ├── uk_train_500.csv
    ├── uk_train_1000.csv
    ├── uk_eval_500.csv
    └── uk_eval2_500.csv
```

---

## Dataset Details

### 1. Non-Curated Dataset (`/non-curated`)

This subset consists of automatic translations generated via Google Translate. It intentionally preserves translation noise, literal renderings of idioms, and cross-linguistic artifacts to simulate realistic low-resource data collection.

- `uk_autotranslate_sarcasm_train.csv` — Full noisy training set
- `uk_autotranslate_sarcasm_test.csv` — Held-out test set for the non-curated baseline

---

### 2. Curated Dataset (`/curated`)

This subset contains human-curated Ukrainian translations. Translation artifacts were manually corrected or removed. English-specific wordplay and culturally bound sarcasm lacking semantic equivalents in Ukrainian were filtered to preserve contextual incongruity while ensuring linguistic naturalness.

The training data is pre-split into fixed sample sizes (100, 200, 500, 1000) to reproduce the sample-efficiency learning curves reported in the paper.

#### Evaluation Sets & Data Leakage Prevention

- `uk_eval_500.csv` — Primary evaluation set for models fine-tuned on the 100, 200, and 500-sample splits.
- `uk_eval2_500.csv` — Strictly isolated evaluation set used exclusively for the 1,000-sample model.

Because `uk_train_1000.csv` was constructed by combining the original `uk_train_500.csv` and `uk_eval_500.csv` to scale the training data, a new evaluation set (`uk_eval2_500.csv`) was created to guarantee zero data leakage during the final 1,000-sample evaluation.

---

## Acknowledgements & Source Dataset

This dataset is a derivative cross-lingual work based on the Irony/Sarcasm subset of the TweetEval benchmark created by Cardiff NLP.

- Original Hugging Face dataset: `cardiffnlp/tweet_eval`
- Original GitHub repository: https://github.com/cardiffnlp/tweeteval

If you use our Ukrainian translations in your research, please also cite the original TweetEval paper:

```bibtex
@inproceedings{barbieri2020tweeteval,
  title={{TweetEval} Benchmark for Tweet Classification},
  author={Barbieri, Francesco and Camacho-Collados, Jose and Espinosa Anke, Luis and Neves, Leonardo},
  booktitle={Findings of the Association for Computational Linguistics: EMNLP 2020},
  year={2020}
}
```

---

## Citation

If you use this dataset or methodology in your research, please cite the accompanying paper:

```bibtex
@misc{trubachova2026alignment,
  title={Overcoming the Alignment Tax: Cross-Lingual Sarcasm Detection with Llama 3 in Low-Resource Contexts},
  author={Trubachova, Anastasiia},
  year={2026},
  eprint={INSERT_ARXIV_ID},
  archivePrefix={arXiv},
  primaryClass={cs.CL}
}
```
