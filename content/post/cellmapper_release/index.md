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
---

Hey everyone! 👋 I'm excited to announce the release of [CellMapper](https://github.com/quadbio/cellmapper), a new tool I've developed for efficient mapping between query and reference datasets. Whether you're working with spatial data, multi-modal integration, or massive reference atlases, CellMapper has got you covered! All you need is a joint latent space for your datasets. 

## What's CellMapper? 🤔

CellMapper is a k-NN-based tool that lets you map cells across different representations to transfer:
- 🏷️ Cell type labels
- 📊 Embeddings 
- 🧬 Expression values

## Performance Optimized for Scale ⚡

CellMapper achieves its efficiency through:
- Accelerated neighborhood search using [faiss](https://github.com/facebookresearch/faiss) or [RAPIDS](https://docs.rapids.ai/) on GPU
- Sparse matrix multiplications for memory-efficient data transfer
- Modular interface that separates neighborhood calculation from data transfer

This architecture enables CellMapper to handle 1.5 million cells in about 30 seconds on a single RTX 4090 with 60 GB of CPU memory—making it practical for working with modern large-scale datasets.

## Cool Things You Can Do With CellMapper 🔍

- 🔄 Transfer cell type labels from dissociated to spatial datasets
- 💫 Map embeddings between query and reference datasets
- 📍 Calculate presence scores for your cells in reference atlases
- 🏙️ Identify cellular niches in spatial data
- 📈 Evaluate your transfers with built-in metrics

## The Math Behind It 🧮

CellMapper is built on a straightforward but powerful approach: k-nearest neighbor (k-NN) graphs with kernels applied to create mapping matrices. Here's how it works:

1. For each query cell, find its k nearest neighbors in the reference dataset 
2. Apply a kernel function to turn these neighbor relationships into weights
3. Use these weights to transfer information from reference to query cells

The method is expressed by the formula:

$$Y_{\text{query}} = M \cdot Y_{\text{reference}}$$

Where $M$ is our mapping matrix derived from the k-NN graph, and $Y_{\text{reference}}$ can represent:
- Categorical data from `.obs` (automatically one-hot encoded)
- Dense arrays from `.obsm` (like UMAP or PCA embeddings)
- Sparse matrices from `.X` or layers (e.g. gene expression data)

This approach is highly flexible and can be applied to virtually any type of data!

## Getting Started in 3 Lines of Code 💻

```python
from cellmapper import CellMapper

cmap = CellMapper(query, reference).fit(
    use_rep="X_joint", obs_keys="celltype", obsm_keys="X_umap", layer_key="X"
)
```

That's it! This will transfer cell types, UMAP embeddings, and expression values from your reference to your query dataset.

## Standing on the Shoulders of Giants 👨‍🔬

The k-NN transfer approach isn't novel — it's a common technique used throughout the field. Among others, CellMapper is heavily inspired by:
- Scanpy's [ingest](https://scanpy.readthedocs.io/en/stable/generated/scanpy.tl.ingest.html) function
- The [HNOCA-tools](https://devsystemslab.github.io/HNOCA-tools/) package

What makes CellMapper different is its focus on efficiency, flexibility, and ease of use. It separates the method (k-NN graph with kernels) from the application (mapping across representations), allowing for greater versatility and performance optimization.

## Why I Built This 💭

Working with datasets across different modalities or platforms presents specific computational challenges — especially when transferring information between them at scale. Existing tools often struggled with either performance on large datasets or flexibility across data types. CellMapper addresses these challenges by:

1. Leveraging high-performance computing libraries for nearest neighbor search
2. Providing flexibility across data types and modalities
3. Offering a clean API with intuitive defaults
4. Integrating tightly with AnnData objects

For more details, tutorials, and examples, check out the [documentation](https://cellmapper.readthedocs.io/) or dive into the [GitHub repo](https://github.com/quadbio/cellmapper)!

Happy mapping! 🗺️
