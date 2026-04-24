# Applied Activity: From Word Embeddings to Semantic Similarity
### US Immigration Policy — Scopus Corpus

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/GloVe-wiki--gigaword--100-orange" alt="GloVe">
  <img src="https://img.shields.io/badge/Corpus-7%20Scopus%20papers-red" alt="Corpus">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License">
</p>

<p align="center">
  <a href="https://eliandmo.github.io/word-embeddings-immigration/">
    <img src="https://img.shields.io/badge/🌐%20Live%20Report-GitHub%20Pages-C8102E?style=for-the-badge" alt="Live Report">
  </a>
  &nbsp;
  <a href="https://colab.research.google.com/github/eliandmo/word-embeddings-immigration/blob/main/word_embeddings_final.ipynb">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab">
  </a>
</p>

---

| | |
|---|---|
| **Student** | Elián David Martínez Orozco |
| **Professor** | Dr. rer. nat. Humberto Llinás |
| **Course** | Fundamentals of AI with Neural Networks and Transformers |
| **Institution** | Universidad del Norte — Barranquilla, Colombia |
| **Year** | 2026 |

---

## About

This repository contains the **Applied Activity** on word embeddings for the course *Fundamentals of AI with Neural Networks and Transformers*. The activity demonstrates the progression from frequency-based representations (Bag-of-Words, TF-IDF) to dense semantic embeddings (GloVe), applied to a corpus of seven peer-reviewed papers on US immigration policy retrieved from **Scopus**.

The full interactive report is published as a [live GitHub Pages site](https://eliandmo.github.io/word-embeddings-immigration/).

---

## Scopus Query

```
"US immigration policy" AND ("border enforcement" OR "visa reform" OR "asylum")
AND (abstract OR research OR paper)
```

---

## Files

```
.
├── index.html                    ← Full HTML report (renders as GitHub Pages)
├── word_embeddings_final.ipynb   ← Jupyter Notebook (12 sections)
└── README.md
```

---

## Corpus

Seven papers retrieved from Scopus covering distinct sub-themes of US immigration policy:

| ID | Authors | Journal | Year |
|----|---------|---------|------|
| P1 | Gonzalez et al. | *Public Health* | 2025 |
| P2 | Galli | *Journal of Borderlands Studies* | 2023 |
| P3 | Kerwin | *Journal on Migration and Human Security* | 2018 |
| P4 | Kerwin & Alulema | *Journal on Migration and Human Security* | 2021 |
| P5 | Argüellová | *Central European Journal of International and Security Studies* | 2015 |
| P6 | Pantoja | *Journal of Ethnic and Migration Studies* | 2006 |
| P7 | Wasem | *Journal on Migration and Human Security* | 2020 |

---

## Notebook Structure

| Section | Content |
|---------|---------|
| **Preprocessing** | 6-step cleaning pipeline · 31–49% token reduction per abstract |
| **§1** | From frequency-based to embedding-based representations |
| **§2** | Embedding model description — GloVe wiki-gigaword-100, 100-dim, 400K vocab |
| **§3** | Corpus definition + vocabulary exploration — 13/15 terms in-vocab |
| **§4** | Nearest neighbors for `asylum`, `deportation`, `enforcement` |
| **§5** | Analogy reasoning: `detention + rights − enforcement ≈ civil` |
| **§6** | Word similarity matrix — 6×6 pairwise cosine |
| **§7** | Text similarity: BoW · TF-IDF · Mean Embeddings |
| **§8** | Word Mover's Distance (WMD) |
| **§9** | Comparison with TF-IDF — all 21 pairs ranked |
| **§10** | Key divergence: where meaning exceeds vocabulary |
| **§11** | Conceptual reflection |
| **§12** | Reproducibility |

---

## Key Results

**BoW:** vocabulary 407 tokens · matrix (7 × 407) · sparsity 82.9%

**Largest divergence between TF-IDF and Mean Embedding cosine:**

| Pair | TF-IDF | Mean Emb | Δ |
|------|--------|----------|---|
| P1 vs P4 — Border Healthcare / Catholic Institutions | 0.0644 | 0.9267 | **+0.8623** |
| P3 vs P5 — IIRIRA / Border Dynamics | 0.0779 | 0.9234 | +0.8455 |
| P3 vs P4 — IIRIRA / Catholic Institutions | 0.0906 | 0.9312 | +0.8406 |

> P1 and P4 describe the same enforcement-driven reality — access barriers, institutional response, immigrant vulnerability — but use different disciplinary vocabularies (public health vs. institutional sociology). TF-IDF sees near-zero overlap (0.0644); GloVe embeddings detect the shared policy context (0.9267). These divergent pairs are where shared *meaning* far exceeds shared *vocabulary*.

---

## Installation

```bash
pip install gensim pot numpy pandas matplotlib seaborn scikit-learn
```

> On first run, gensim automatically downloads `glove-wiki-gigaword-100` (~130 MB) and caches it locally. All subsequent runs use the local cache.

---

## Reproducibility

- Random seed: `np.random.seed(42)`
- All code is self-contained — no external scripts required
- Abstracts reproduced verbatim from Scopus export
