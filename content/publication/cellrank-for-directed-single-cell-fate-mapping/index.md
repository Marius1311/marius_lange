---
title: CellRank for directed single-cell fate mapping
publication_types:
  - "2"
authors:
  - Marius Lange
  - Volker Bergen
  - Michal Klein
  - Manu Setty
  - Bernhard Reuter
  - Mostafa Bakhti
  - Heiko Lickert
  - Meshal Ansari
  - Janine Schniering
  - Herbert B Schiller
  - Dana Pe’er
  - Fabian J Theis
doi: https://doi.org/10.1038/s41592-021-01346-6
publication: https://www.nature.com/articles/s41592-021-01346-6
publication_short: Nature Methods
abstract: Computational trajectory inference enables the reconstruction of cell
  state dynamics from single-cell RNA sequencing experiments. However,
  trajectory inference requires that the direction of a biological process is
  known, largely limiting its application to differentiating systems in normal
  development. Here, we present CellRank (https://cellrank.org) for single-cell
  fate mapping in diverse scenarios, including regeneration, reprogramming and
  disease, for which direction is unknown. Our approach combines the robustness
  of trajectory inference with directional information from RNA velocity, taking
  into account the gradual and stochastic nature of cellular fate decisions, as
  well as uncertainty in velocity vectors. On pancreas development data,
  CellRank automatically detects initial, intermediate and terminal populations,
  predicts fate potentials and visualizes continuous gene expression trends
  along individual lineages. Applied to lineage-traced cellular reprogramming
  data, predicted fate probabilities correctly recover reprogramming outcomes.
  CellRank also predicts a new dedifferentiation trajectory during postinjury
  lung regeneration, including previously unknown intermediate cell states,
  which we confirm experimentally.
draft: false
featured: true
tags:
  - CellRank
  - Fate mapping
  - Markov chains
  - RNA velocity
  - Trajectory inference
  - scRNA-seq
image:
  filename: featured.jpeg
  focal_point: Smart
  preview_only: false
  caption: "CellRank uses both RNA velocity and transcriptomic similarity to infer
    directed cellular trajectories beyond normal development. "
date: 2022-06-06T14:56:54.782Z
---
