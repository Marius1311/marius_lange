---
title: moscot preprint out
subtitle: Mapping cells through time and space with moscot
date: 2023-05-14T12:57:18.125Z
summary: ""
draft: false
featured: true
authors:
  - admin
lastmod: 2023-05-14T12:57:18.125Z
tags:
  - moscot, spatial, spatiotemporal, CellRank, alignment, optimal transport, ott
categories:
  - News
projects: []
image:
  caption:
  focal_point: ""
  placement: 2
  preview_only: false
  filename: featured.jpg
---
We've just released moscot, our new computational framework that maps single cells across time and space using efficient optimal transport algorithms. Importantly, moscot makes use of multi-modal information consistently across all applications, scales to atlases, and comes with a modular and extensible implementation. To find out more, see the tweetorials [from Dominik](https://twitter.com/Dominik1Klein/status/1657030449053458435) or [me](https://twitter.com/MariusLange8/status/1657046851860721664), or read the full [preprint](https://www.biorxiv.org/content/10.1101/2023.05.11.540374v2) on bioRxiv. Check out the implementation at [moscot-tools.org](https://moscot-tools.org) to try it on your own single-cell or spatial data.

This project was co-lead by [Dominik Klein](https://twitter.com/Dominik1Klein), [Giovanni Palla](https://twitter.com/g_palla1), and me from the [Theislab](https://www.helmholtz-munich.de/en/icb/research-groups/theis-lab), as well as Michal Klein from Apple ML Research and [Zoe Piran](https://twitter.com/zoe_piran) from the [Nitzan lab](https://www.nitzanlab.com/)



Abstract
--------
Single-cell genomics technologies enable multimodal profiling of millions of cells across temporal and spatial dimensions. Experimental limitations prevent the measurement of all-encompassing cellular states in their native temporal dynamics or spatial tissue niche. Optimal transport theory has emerged as a powerful tool to overcome such constraints, enabling the recovery of the original cellular context. However, most algorithmic implementations currently available have not kept up the pace with increasing dataset complexity, so that current methods are unable to incorporate multimodal information or scale to single-cell atlases. Here, we introduce multi-omics single-cell optimal transport (moscot), a general and scalable framework for optimal transport applications in single-cell genomics, supporting multimodality across all applications. We demonstrate moscot's ability to efficiently reconstruct developmental trajectories of 1.7 million cells of mouse embryos across 20 time points and identify driver genes for first heart field formation. The moscot formulation can be used to transport cells across spatial dimensions as well: To demonstrate this, we enrich spatial transcriptomics datasets by mapping multimodal information from single-cell profiles in a mouse liver sample, and align multiple coronal sections of the mouse brain. We then present moscot.spatiotemporal, a new approach that leverages gene expression across spatial and temporal dimensions to uncover the spatiotemporal dynamics of mouse embryogenesis. Finally, we disentangle lineage relationships in a novel murine, time-resolved pancreas development dataset using paired measurements of gene expression and chromatin accessibility, finding evidence for a shared ancestry between delta and epsilon cells. Moscot is available as an easy-to-use, open-source python package with extensive documentation at https://moscot-tools.org.
