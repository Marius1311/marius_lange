---
title: Mapping lineage-traced cells across time points with moslin
publication_types:
  - "3"
authors:
  - Marius Lange
  - Zoe Piran
  - Michal Klein
  - Bastiaan Spanjaard
  - Dominik Klein
  - Jan Philipp Junker
  - Fabian J. Theis
  - Mor Nitzan
doi: https://doi.org/10.1101/2023.04.14.536867
publication: bioRxiv
publication_short: bioRxiv
abstract:
  Simultaneous profiling of single-cell gene expression and lineage history holds enormous potential for studying cellular decision-making beyond simpler pseudotime-based approaches. However, it is currently unclear how lineage and gene expression information across experimental time points can be combined in destructive experiments, which is particularly challenging for in-vivo systems. Here we present moslin, a Fused Gromov-Wasserstein-based model to couple matching cellular profiles across time points. In contrast to existing methods, moslin leverages both intra-individual lineage relations and inter-individual gene expression similarity. We demonstrate on simulated and real data that moslin outperforms state-of-the-art approaches that use either one or both data modalities, even when the lineage information is noisy. On C. elegans embryonic development, we show how moslin, combined with trajectory inference methods, predicts fate probabilities and putative decision driver genes. Finally, we use moslin to delineate lineage relationships among transiently activated fibroblast states during zebrafish heart regeneration. We anticipate moslin to play a crucial role in deciphering complex state change trajectories from lineage-traced single-cell data.
draft: false
featured: True
tags:
  - moslin
  - lineage tracing
  - Dynamics
  - Trajectory inference
  - scLT
  - CellRank
  - moscot
image:
  filename: featured
  caption: "moslin combines gene expression with lineage tracing information to reconstruct complex differentiation trajectories. Figure created with BioRender. "
  focal_point: Smart
  preview_only: false
date: 2023-04-17T15:46:10.280Z
url_code: https://github.com/theislab/moslin
---
