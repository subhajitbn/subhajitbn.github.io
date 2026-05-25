---
layout: default
title: Genelit
---

# Genelit: PubMed literature status of cancer-associated genes
A small but handy tool, built to help scientists quickly perform a literature review on a set of genes associated with a particular cancer type.

- [Code](https://github.com/subhajitbn/GeneLit)
- [Live](https://genelit.streamlit.app/)

### Why
In my own cancer biomarker research, I often found myself manually checking PubMed for gene relevance. This is a slow and repetitive process. GeneLit is a fast, minimal tool to generate a PubMed literature status for a list of genes, with filters for cancer type, synonyms, and publication dates.

### Features
- Easy-to-fill input form for genes, cancer type, and time range
- Optional email and API key input for faster PubMed querying
- Automatic retries on occasional network failures
- Clean output with novel gene indication and recent PubMed IDs
