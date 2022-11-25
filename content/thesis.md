---
title: Thesis
date: '2022-11-24T00:00:00+01:00'
draft: false
share: false
commentable: false
editable: false

# Optional header image (relative to `static/media/` folder).
header:
  caption: ''
  image: ''
---
My PhD thesis was focused on learning the dynamical aspects of biological processes based on single-cell genomics data. You find the abstract below and the full text in the [online library](https://mediatum.ub.tum.de/1656496) of the Technical University of Munich (TUM).

## Abstract

Cells dynamically change their molecular state in many situations, including development, the cell cycle, the circadian rhythm, and regeneration. Single-cell assays allow us to describe this state with unprecedented resolution; for example, single-cell RNA sequencing (scRNA-seq) quantifies the expression level of all genes. However, cells are destroyed upon sequencing, making it difficult to use these assays to study continuous processes that ideally require us to measure the same cell a few times. This fundamental difficulty has fueled the development of many mathematical methods that use ensembles of single cells at different internal states to reconstruct the average trajectory of a "typical cell," a concept known as *trajectory inference*. Recent experimental innovations, including RNA velocity ([La Manno et al., Nature 2018](https://www.nature.com/articles/s41586-018-0414-6) and [Bergen et al., Nature Biotechnology 2020](https://www.nature.com/articles/s41587-020-0591-3)) and lineage-tracing assays (see e.g. [Sankaran, Weissman and Zon, Science 2022](https://www.science.org/doi/10.1126/science.abm5874) or [Wagner and Klein, Nature Reviews Genetics 2020](https://www.nature.com/articles/s41576-020-0223-2)), provide new opportunities to improve trajectory inference; however, their harmonization with established modeling paradigms presents new mathematical challenges that need to be addressed.

The first innovation we considered in this thesis is RNA velocity; a strategy to estimate the direction of expression changes based on the ratio of nascent versus mature transcripts. Essentially, RNA velocity approximates a high-dimensional vector field in the state manifold which points in a cell's future direction. We introduced the [CellRank](https://cellrank.org) ([Lange et al., Nature Methods 2022](https://www.nature.com/articles/s41592-021-01346-6)) framework and showed how it combines RNA velocity with expression similarity into a Markov chain to robustly estimate initial and terminal states of cellular state changes as well as fate probabilities and driver genes. Applied to regeneration and reprogramming data examples, we showed how CellRank generalizes trajectory inference beyond normal development, a setting that most previous methods were limited to. The assumptions of the RNA velocity model do not hold in every biological system; in an effort to make CellRank widely applicable, we extended it towards other estimates of directed differentiation, thus transforming CellRank into a unified framework for single-cell fate mapping.

The second innovation we considered is lineage-traced scRNA-seq data which simultaneously contains molecular state and clonal history. We introduced moslin, an optimal-transport-based method to efficiently combine lineage with gene expression information to obtain more accurate couplings of cells across time points. On simulated data, we confirmed that this strategy recovers ground-truth couplings more accurately compared to methods that only use gene expression or lineage information and competing methods that combine both sources of information. Applied to *C. elegans* developmental data, we showed how a combination of moslin with CellRank recovered known decision driver genes. For time-course data with only gene expression information, we greatly accelerated previous approaches and made them applicable to much larger datasets. moslin is part of moscot, a new spatio-temporal framework for scalable optimal transport applications in single-cell genomics.

CellRank and moslin extend trajectory inference towards new experimental approaches and massive datasets. They enable gaining a deeper understanding of dynamical processes in biology based on single-cell genomics assays.
