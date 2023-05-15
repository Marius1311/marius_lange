---
title: Mapping cells through time and space with moscot
publication_types:
  - "3"
authors:
  - Dominik Klein
  - Giovanni Palla
  - Marius Lange
  - Michal Klein
  - Zoe Piran
  - Manuel Gander
  - Laetitia Meng-Papaxanthos
  - Michael Sterr
  - Aimee Bastidas-Ponce
  - Marta Tarquis-Medina
  - Heiko Lickert
  - Mostafa Bakhti
  - Mor Nitzan
  - Marco Cuturi
  - Fabian J. Theis
doi: https://doi.org/10.1101/2023.05.11.540374
publication: bioRxiv
publication_short: bioRxiv
abstract:
  Single-cell genomics technologies enable multimodal profiling of millions of cells across temporal and spatial dimensions. Experimental limitations prevent the measurement of all-encompassing cellular states in their native temporal dynamics or spatial tissue niche. Optimal transport theory has emerged as a powerful tool to overcome such constraints, enabling the recovery of the original cellular context. However, most algorithmic implementations currently available have not kept up the pace with increasing dataset complexity, so that current methods are unable to incorporate multimodal information or scale to single-cell atlases. Here, we introduce multi-omics single-cell optimal transport (moscot), a general and scalable framework for optimal transport applications in single-cell genomics, supporting multimodality across all applications. We demonstrate moscot's ability to efficiently reconstruct developmental trajectories of 1.7 million cells of mouse embryos across 20 time points and identify driver genes for first heart field formation. The moscot formulation can be used to transport cells across spatial dimensions as well. To demonstrate this, we enrich spatial transcriptomics datasets by mapping multimodal information from single-cell profiles in a mouse liver sample, and align multiple coronal sections of the mouse brain. We then present moscot.spatiotemporal, a new approach that leverages gene expression across spatial and temporal dimensions to uncover the spatiotemporal dynamics of mouse embryogenesis. Finally, we disentangle lineage relationships in a novel murine, time-resolved pancreas development dataset using paired measurements of gene expression and chromatin accessibility, finding evidence for a shared ancestry between delta and epsilon cells. Moscot is available as an easy-to-use, open-source python package with extensive documentation at https://moscot-tools.org.
draft: false
featured: True
tags:
  - Moscot
  - Optimal transport
  - spatiotemporal
  - Mapping
  - alignment
  - CCF
image:
  filename: featured
  caption: "moscot mapps cells through time and space using efficient optimal transport algorithms."
  focal_point: Smart
  preview_only: false
date: 2023-04-17T15:46:10.280Z
url_code: https://moscot-tools.org
---
