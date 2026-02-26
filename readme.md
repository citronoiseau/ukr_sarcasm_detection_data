# 🌍 Cross-Lingual Sarcasm Detection: Ukrainian Sarcasm Dataset

[![Paper](https://img.shields.io/badge/Paper-ResearchGate-00ccbb.svg)](<[INSERT_RESEARCHGATE_URL_HERE](https://www.researchgate.net/publication/401229173_Overcoming_the_Alignment_Tax_Cross-Lingual_Sarcasm_Detection_with_Llama_3_in_Low-Resource_Contexts)>)
[![Dataset](https://img.shields.io/badge/Dataset-tweet__eval-blue)](#)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-green)](#)

## This repository contains the training and evaluation datasets used in the preprint: **[Overcoming the Alignment Tax: Cross-Lingual Sarcasm Detection with Llama 3 in Low-Resource Contexts](https://www.researchgate.net/publication/401229173_Overcoming_the_Alignment_Tax_Cross-Lingual_Sarcasm_Detection_with_Llama_3_in_Low-Resource_Contexts)**.

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

This dataset consists of a primary training set and a strictly isolated evaluation set to guarantee zero data leakage during the final evaluation:

- **`uk_train_1000.csv`**: The full curated training set consisting of 1,000 contextual, human-verified sentences.
- **`uk_eval_500.csv`**: An isolated evaluation set consisting of 500 sentences, used to test the model fine-tuned on the curated training data.

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
  publisher={ResearchGate},
  doi={10.13140/RG.2.2.25540.08327},
  url={https://www.researchgate.net/publication/401229173_Overcoming_the_Alignment_Tax_Cross-Lingual_Sarcasm_Detection_with_Llama_3_in_Low-Resource_Contexts}
}
```
