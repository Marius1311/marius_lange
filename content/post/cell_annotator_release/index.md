---
title: "AI-Powered Cell Type Annotation for scRNA-seq Data with CellAnnotator"
subtitle: "A new tool for automatic annotation of single-cell RNA sequencing data using OpenAI models"
date: 2025-04-20T12:00:00Z
summary: ""
draft: false
featured: true
authors:
  - admin
lastmod: 2025-04-20T12:00:00Z
tags:
  - scRNA-seq
  - cell annotation
  - AI
  - OpenAI
  - bioinformatics
  - scverse
categories:
  - News
  - Software
projects: []
---

Tired of manually annotating cell types in your single-cell datasets? I'm thrilled to announce [CellAnnotator](https://github.com/quadbio/cell-annotator), a new tool that harnesses the power of large language models to automate one of the most time-consuming steps in scRNA-seq analysis. As part of the [scverse ecosystem](https://scverse.org/packages/#ecosystem), CellAnnotator interprets marker gene patterns to generate consistent cell type annotations with less human intervention. This works well for many systems where vast prior knowledge is available, but has limitations in less well studied systems. Also, you'll still need to validate and fine-tune your annotations. So use with care. 

## What is CellAnnotator?

Cell type annotation is often a bottleneck in single-cell analysis workflows. CellAnnotator addresses this challenge by analyzing marker genes through large language models to provide automated, consistent cell type annotations.

### Key Features

- **Automated cell type prediction** with cell state and confidence scores
- **Harmonized annotations** across multiple samples
- **Integration of prior knowledge** about your biological system
- **Structured outputs** for reliable and consistent results
- **Free to try** using OpenAI's free tier with gpt-4o-mini

### Simple Usage Example

```python
from cell_annotator import CellAnnotator

cell_ann = CellAnnotator(
    adata, 
    species="human", 
    tissue="heart", 
    cluster_key="leiden", 
    sample_key="samples",
).annotate_clusters()
```

For installation instructions, detailed usage guides, and tutorials, please visit the [documentation](https://cell-annotator.readthedocs.io) or the [GitHub repository](https://github.com/quadbio/cell-annotator).

## Credits

This tool was inspired by [Hou et al., Nature Methods 2024](https://www.nature.com/articles/s41592-024-02235-4) and builds upon ideas from [GPTCellAnnotator](https://github.com/VPetukhov/GPTCellAnnotator).
