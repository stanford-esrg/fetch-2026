# "Stop trying to make fetch happen": Towards a Modality-Aware Understanding of Unnecessary Resources on the Web

Artifact for the paper:

> **"Stop trying to make fetch happen": Towards a Modality-Aware Understanding of Unnecessary Resources on the Web.** *Proceedings of the ACM Internet Measurement Conference (IMC)*, 2026. Rumaisa Habib, Balaji Balachandran, Nurullah Demir, and Zakir Durumeric.

```bibtex
@inproceedings{habib2026fetch,
  title={"Stop trying to make fetch happen": Towards a Modality-Aware Understanding of Unnecessary Resources on the Web},
  author={Habib, Rumaisa and Balachandran, Balaji and Demir, Nurullah and Durumeric, Zakir},
  booktitle={Proceedings of the ACM Internet Measurement Conference},
  year={2026}
}
```

This directory contains the crawl data and analysis notebook needed to reproduce the results in the paper.

## What's included

```
fetch-2026/
├── analysis.ipynb              # single notebook that produces all paper plots/results
├── requirements.txt            # pinned Python dependencies
├── data/
│   ├── domain_popularity.csv       # (rank, origin)
│   ├── domain_categories.csv       # automatically assigned content categories per domain
│   ├── domain_categories_manual.csv# manually verified/corrected categories (takes precedence)
│   ├── functionality_test_urls.csv # URL subset selected for functionality-preservation testing
│   └── all_urls.txt                # full list of URLs included in the crawl
├── results/
│   ├── basic/                   # crawl results without functionality reload/comparison
│   │   └── results_basic_{0..7}.jsonl.gz
│   └── functional/              # crawl results including the functionality testing
│       └── functional_results_{0..59}.jsonl.gz
└── graphs/                      # output figures (written here when the notebook runs)
```

Each `.jsonl.gz` file is a gzip-compressed JSONL file with one JSON record per crawled page, with per-stage similarity metrics (textual, structural, visual, functional) plus resource counters used throughout the analysis. The analysis file reads these files directly; no need to decompress. 

## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Reproducing the paper's results

Open `analysis.ipynb` and run all cells top to bottom:

```bash
jupyter notebook analysis.ipynb
```

All paths inside the notebook are relative to this directory, so no configuration is needed. Every figure referenced in the paper is written to `graphs/` (created automatically), and every reported statistic is printed inline as the notebook runs.
