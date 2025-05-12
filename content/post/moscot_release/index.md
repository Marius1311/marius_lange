---
title: "🚀 Introducing Moscot: Multiomics Single-Cell Optimal Transport"
subtitle: "Map cells through time and space with scalable optimal transport! ⚡"
date: 2025-05-12T14:00:00Z
summary: ""
draft: false
featured: true
authors:
  - admin
lastmod: 2025-05-12T14:00:00Z
tags:
  - single-cell
  - optimal transport
  - spatiotemporal
  - multimodal
  - bioinformatics
categories:
  - News
  - Software
projects: []
---

Hey everyone! 👋 Understanding cellular dynamics across time and space is one of the most challenging tasks in single-cell genomics. Today I'm thrilled to introduce [Moscot](https://github.com/theislab/moscot), a powerful framework that uses optimal transport theory to map cells through time and space. Whether you're tracing developmental trajectories, mapping spatial organization, aligning tissue sections, or integrating multimodal data, Moscot makes these complex tasks both intuitive and computationally efficient.

## What's Moscot? 🤔

Moscot (Multiomics Single-Cell Optimal Transport) is a framework that solves a wide range of single-cell analysis challenges:
- 🔄 Trajectory inference across time points
- 🗺️ Spatial mapping of cells
- 📊 Multimodal data integration
- 🧩 Alignment of spatial transcriptomics slides
- 📈 Handling of lineage information 

## Performance Optimized for Scale ⚡

Moscot achieves unprecedented scalability through:
- Low-rank optimal transport for computational efficiency
- Just-in-time compilation via JAX
- GPU acceleration for large datasets
- Linear memory complexity

This architecture enables Moscot to handle millions of cells—we've successfully mapped 1.7 million cells of mouse embryos across 20 time points in our publication!

## Cool Things You Can Do With Moscot 🔍

- 🧬 Reconstruct developmental trajectories with temporal, spatial, and lineage information
- 🔬 Map cells to their spatial organization
- 📱 Enhance spatial transcriptomics by transferring information from single-cell profiles
- 🔗 Align multiple spatial transcriptomics slides
- 🔄 Translate between different modalities (RNA, ATAC, protein)

## The Math Behind It 🧮

Moscot is built on optimal transport (OT) theory, a mathematical framework for comparing probability distributions. In single-cell analysis, we view cell populations as distributions and use OT to find mappings between them.

The core of OT involves finding a coupling matrix that minimizes the transportation cost:

$$\min_{\gamma \in \Pi(\mu, \nu)} \langle \gamma, C \rangle$$

Where:
- $\gamma$ is the coupling matrix
- $C$ is the cost matrix (distances between cells)
- $\mu$ and $\nu$ are the source and target distributions

Moscot extends this with regularization, multimodal integration, and problem-specific constraints to create a flexible framework for single-cell analysis.

## Getting Started in 3 Lines of Code 💻

```python
import moscot as mt

problem = mt.problems.time.TemporalProblem(adata)
problem.prepare(time_key="day", joint_attr="X_pca")
problem.solve()
```

That's it! From here you can visualize transitions, extract insights, and analyze cellular dynamics.

## Standing on the Shoulders of Giants 👨‍🔬

Moscot is powered by [OTT (Optimal Transport Tools)](https://ott-jax.readthedocs.io/), a JAX-based toolkit that enables just-in-time compilation, GPU acceleration, and automatic differentiation. Our work builds upon foundational contributions from the optimal transport community, particularly the work of [Marco Cuturi](https://www.gpeyre.com/publications/) and collaborators on computational OT.

## Why We Built This 💭

Working with increasingly complex single-cell datasets presented specific computational challenges:

1. **Scale**: Traditional OT methods couldn't handle millions of cells
2. **Multimodality**: Existing tools struggled to integrate multiple data modalities
3. **Fragmentation**: Different OT applications required different tools
4. **Complexity**: Advanced OT features were difficult to implement

Moscot addresses these challenges by providing a unified, scalable framework that supports multimodality across all applications.

## Real Insights from Real Data 📊

In our [Nature paper](https://www.nature.com/articles/s41586-024-08453-2), we demonstrated Moscot's capabilities on several challenging problems:

- Reconstructing developmental trajectories of 1.7 million mouse embryo cells
- Identifying driver genes for first heart field formation
- Mapping multimodal information to spatial liver data
- Aligning multiple coronal sections of the mouse brain
- Revealing new insights into pancreatic epsilon and delta cell development

For more details, tutorials, and examples, check out the [documentation](https://moscot.readthedocs.io/) or dive into the [GitHub repo](https://github.com/theislab/moscot)!

Happy mapping! 🗺️