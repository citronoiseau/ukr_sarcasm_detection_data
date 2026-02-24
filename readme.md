# Cross-Lingual Sarcasm Detection: Ukrainian Sarcasm Dataset

This repository contains the training and evaluation datasets used in the preprint: **[Overcoming the Alignment Tax: Cross-Lingual Sarcasm Detection with Llama 3 in Low-Resource Contexts](INSERT_ARXIV_LINK)**.

## Overview

This repository provides two distinct datasets designed to evaluate cross-lingual abstract reasoning and the "alignment tax" in Large Language Models. Both datasets are derived from the Irony/Sarcasm subset of the `tweet_eval` corpus and have been sanitized to remove explicit lexical shortcuts (e.g., `#sarcasm`, `#irony`, emojis).

The data is split into two primary methodologies to allow researchers to compare the impact of data quality on cross-lingual transfer: **Non-Curated** (machine-translated) and **Curated** (human-verified).

## Repository Structure

```text
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

## Dataset Details & Evaluation Strategy

### 1. Non-Curated Data (`/non-curated`)

This subset contains automatic machine translations (via Google Translate). It introduces noise and literal translations of English-specific idioms to simulate raw, low-resource data gathering.

- **`uk_autotranslate_sarcasm_train.csv`**: The full noisy training set.
- **`uk_autotranslate_sarcasm_test.csv`**: The held-out test set for the non-curated baseline.

### 2. Curated Data (`/curated`)

This subset contains human-curated translations. Translation artifacts were manually filtered, and culturally bound English wordplay lacking direct semantic equivalents in Ukrainian was removed to ensure high-quality contextual incongruity.

The training data is pre-split into defined sample sizes (100, 200, 500, 1000) to replicate the sample-efficiency learning curves reported in the paper.

**Evaluation Sets & Data Leakage Prevention:**

- **`uk_eval_500.csv`**: The primary evaluation set used to test models fine-tuned on the 100, 200, and 500-sample training splits.
- **`uk_eval2_500.csv`**: A strictly isolated evaluation set created specifically for evaluating the `uk_train_1000.csv` model. **Note:** Because the 1,000-sample training set (`uk_train_1000.csv`) was constructed by blending the original `uk_train_500.csv` and `uk_eval_500.csv` datasets to scale the training size, `uk_eval2_500.csv` was specifically generated to serve as a fresh, unseen test set. This guarantees zero data leakage during the final 1,000-sample evaluation phase.
