---
title: CellRank for directed single-cell fate mapping (ISMB/ECCB)
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
location: ISMB/ECCB
date: 2021-07-12T16:00:04.340Z
date_end: 2021-07-11T22:00:00.000Z
all_day: false
event: Watch the recording on YouTube
event_url: https://www.youtube.com/watch?v=tSfeDZGnZto
publishDate: 2022-06-07T16:00:04.351Z
draft: false
featured: false
authors:
  - admin
tags:
  - CellRank
  - ISMB
  - Trajectory inference
  - RNA velocity
  - Fate mapping
image:
  filename: featured
  caption: "CellRank uses RNA velocity directly in high dimensions to map the
  fate of single cells. Watch the recorded talk on [YouTube](https://www.youtube.com/watch?v=tSfeDZGnZto)"
  focal_point: Smart
  preview_only: false
---
Find our paper in [Nature methods](https://www.nature.com/articles/s41592-021-01346-6) and the code on [github](https://cellrank.readthedocs.io/en/stable/).
