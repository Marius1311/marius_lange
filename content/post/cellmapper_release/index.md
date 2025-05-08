---
title: "🚀 Introducing CellMapper: Lightning-Fast Cell Mapping Across Datasets"
subtitle: "Transfer labels, embeddings, and expression values between datasets in seconds! ⚡"
date: 2025-05-08T14:00:00Z
summary: ""
draft: false
featured: true
authors:
  - admin
lastmod: 2025-05-08T14:00:00Z
tags:
  - single-cell
  - spatial
  - kNN
  - mapping
  - bioinformatics
categories:
  - News
  - Software
projects: []
image:
  caption: 
  focal_point: ""
  placement: 2
  preview_only: false
  filename: featured.png
---

Hey everyone! 👋 I'm super excited to announce the release of [CellMapper](https://github.com/quadbio/cellmapper), a new tool I've developed for lightning-fast mapping between cell datasets. Whether you're working with spatial data, multi-modal integration, or massive reference atlases, CellMapper has got you covered!

## What's CellMapper? 🤔

CellMapper is a k-NN-based tool that lets you map cells across different representations to transfer:
- 🏷️ Cell type labels
- 📊 Embeddings 
- 🧬 Expression values

The best part? It's FAST! ⚡ We're talking about 30 seconds to transfer cell type labels between 1.5 million cells on a single GPU. That's right—millions of cells, no problem!

## Cool Things You Can Do With CellMapper 🔍

- 🔄 Transfer cell type labels from dissociated to spatial datasets
- 💫 Map embeddings between query and reference datasets
- 📍 Calculate presence scores for your cells in reference atlases
- 🏙️ Identify cellular niches in spatial data
- 📈 Evaluate your transfers with built-in metrics

## The Math Behind It (But Simple!) 🧮

CellMapper is built on a straightforward but powerful idea: k-nearest neighbor (k-NN) graphs with kernels applied to create mapping matrices. Here's how it works:

1. For each query cell, find its k nearest neighbors in the reference dataset
2. Apply a kernel function to turn these neighbor relationships into weights
3. Use these weights to transfer information from reference to query cells

The magic is in the simple formula:

$$Y_{\text{query}} = M \cdot Y_{\text{reference}}$$

Where $M$ is our mapping matrix derived from the k-NN graph, and $Y$ contains the values we want to transfer. This approach is super flexible and can be applied to virtually any type of data!

## Getting Started in 3 Lines of Code 💻

```python
from cellmapper import CellMapper

cmap = CellMapper(query, reference).fit(
    use_rep="X_joint", obs_keys="celltype", obsm_keys="X_umap", layer_key="X"
)
```

That's it! This will transfer cell types, UMAP embeddings, and expression values from your reference to your query dataset.

## New in v0.1.3! 🎉

- ✨ Self-mapping mode when you only have a query dataset
- 🌌 Spatial contextualization for niche identification
- 📥 Import pre-computed neighborhoods and transferred expression
- 👨‍👩‍👧‍👦 Equal-weight kernel option for different mapping strategies

## Why I Built This 💭

Working with datasets across different modalities or platforms can be challenging—especially when trying to transfer information between them. Existing tools were either too slow for large datasets or too inflexible. CellMapper solves these problems by being:

1. Super fast (thanks to [faiss](https://github.com/facebookresearch/faiss)!)
2. Flexible across data types and modalities
3. Simple to use with a clean API
4. Tightly integrated with AnnData objects

For more details, tutorials, and examples, check out the [documentation](https://cellmapper.readthedocs.io/) or dive into the [GitHub repo](https://github.com/quadbio/cellmapper)!

Happy mapping! 🗺️
