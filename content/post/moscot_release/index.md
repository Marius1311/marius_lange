---
title: "Introducing Moscot: Multiomics Single-Cell Optimal Transport"
subtitle: "A framework for mapping cells through time and space using scalable optimal transport"
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

## Introduction to Moscot

Moscot (Multiomics Single-Cell Optimal Transport) is a comprehensive framework developed to address complex challenges in single-cell analysis:
- Trajectory inference across time points
- Spatial mapping of cells
- Multimodal data integration
- Alignment of spatial transcriptomics slides
- Integration of lineage information

## Computational Efficiency for Large-Scale Analysis

Moscot achieves unprecedented scalability through several computational innovations:
- Low-rank optimal transport for reduced complexity
- Just-in-time compilation via JAX for accelerated execution
- GPU acceleration for parallel processing
- Linear memory complexity algorithms

This computational architecture enables Moscot to process datasets of unprecedented scale—our recent work successfully mapped 1.7 million cells across 20 time points of mouse embryonic development.

## Mathematical Foundations

Moscot is built on the mathematical theory of optimal transport (OT), a framework originally formulated by Gaspard Monge in the 18th century and later extended by Leonid Kantorovich.

### The Optimal Transport Problem

In its basic formulation, optimal transport considers two probability distributions $\mu$ and $\nu$ supported on spaces $\mathcal{X}$ and $\mathcal{Y}$, respectively. The objective is to find a transport plan $\gamma \in \Pi(\mu, \nu)$ that minimizes the transportation cost:

$$\min_{\gamma \in \Pi(\mu, \nu)} \int_{\mathcal{X} \times \mathcal{Y}} c(x, y) d\gamma(x, y)$$

Where:
- $\Pi(\mu, \nu)$ is the set of joint distributions with marginals $\mu$ and $\nu$
- $c(x, y)$ is the cost function representing the distance between points $x \in \mathcal{X}$ and $y \in \mathcal{Y}$

In the context of single-cell analysis, $\mu$ and $\nu$ represent distributions of cells from different conditions, time points, or spatial locations.

### Entropy-Regularized Optimal Transport

To improve computational tractability, Moscot implements entropy-regularized optimal transport, formulated as:

$$\min_{\gamma \in \Pi(\mu, \nu)} \int_{\mathcal{X} \times \mathcal{Y}} c(x, y) d\gamma(x, y) + \varepsilon KL(\gamma || \mu \otimes \nu)$$

Where:
- $\varepsilon$ is the regularization parameter
- $KL(\gamma || \mu \otimes \nu)$ is the Kullback-Leibler divergence between the transport plan and the product of the marginals

This regularization leads to the Sinkhorn algorithm, which can be efficiently implemented through matrix scaling operations:

$$\gamma_{i,j} = \text{diag}(\mathbf{u}) \cdot K \cdot \text{diag}(\mathbf{v})$$

Where $K = e^{-C/\varepsilon}$, and $\mathbf{u}$ and $\mathbf{v}$ are vectors obtained through iterative scaling.

### Low-Rank Optimal Transport

For large-scale problems, Moscot implements low-rank approximations of the transport plan:

$$\gamma_{i,j} \approx \sum_{k=1}^{r} \alpha_k(i) \beta_k(j)$$

Where $r$ is the rank of the approximation, and $\alpha_k$ and $\beta_k$ are basis vectors. This reduces the computational complexity from $\mathcal{O}(n^2)$ to $\mathcal{O}(nr)$, where $n$ is the number of cells.

## Implementation and Usage

Moscot is implemented as a Python package with a clear API. A basic workflow for temporal analysis:

```python
import moscot as mt

problem = mt.problems.time.TemporalProblem(adata)
problem.prepare(time_key="day", joint_attr="X_pca")
problem.solve(epsilon=0.05, rank=100, batch_size=2000)

# Analyze cell transitions
transitions = problem.cell_transitions

# Extract temporal couplings
couplings = problem.get_coupling(source_idx=0, target_idx=1)
```

## Technical Foundation

Moscot is built on [OTT (Optimal Transport Tools)](https://ott-jax.readthedocs.io/), a JAX-based toolkit that provides:

- Just-in-time compilation for computational efficiency
- Automatic differentiation for gradient-based optimization
- GPU/TPU acceleration for parallel processing
- Linear memory complexity solvers

## Addressing Computational Challenges

The development of Moscot was motivated by several technical limitations in the field:

1. **Computational Scalability**: Traditional optimal transport methods have $\mathcal{O}(n^2)$ complexity, making them impractical for modern single-cell datasets with millions of cells. Moscot's implementation reduces this to $\mathcal{O}(nr)$ with low-rank approximations.

2. **Multimodal Integration**: Existing tools lacked a unified framework for incorporating multiple data modalities. Moscot formulates a generalized cost function that integrates information from different modalities:

   $$c_{total}(x, y) = \sum_{m \in M} w_m \cdot c_m(x_m, y_m)$$

   Where $M$ is the set of modalities, $w_m$ are modality weights, and $c_m$ are modality-specific cost functions.

3. **Methodological Fragmentation**: Different optimal transport applications required different tools. Moscot unifies these through a consistent API and a modular design that supports:
   - Temporal mapping with the Wasserstein metric
   - Spatial reconstruction with geometric constraints
   - Multi-section alignment with geometric regularization
   - Modality translation with unbalanced transport formulations

## Applications and Results

In our [Nature paper](https://www.nature.com/articles/s41586-024-08453-2), we demonstrated the capabilities of Moscot on several complex problems:

1. **Large-scale Developmental Trajectories**: Reconstructed trajectories across 1.7 million cells from mouse embryos, employing a structured batch processing approach to overcome memory limitations:

   $$\gamma = \left[ \begin{array}{cccc}
   \gamma_{1,1} & \gamma_{1,2} & \cdots & \gamma_{1,T} \\
   \gamma_{2,1} & \gamma_{2,2} & \cdots & \gamma_{2,T} \\
   \vdots & \vdots & \ddots & \vdots \\
   \gamma_{T,1} & \gamma_{T,2} & \cdots & \gamma_{T,T}
   \end{array} \right]$$

   Where each block $\gamma_{i,j}$ represents the coupling between time points $i$ and $j$.

2. **Spatial Reconstruction**: Formulated as a problem with geometric constraints:

   $$\min_{\gamma \in \Pi(\mu, \nu)} \langle \gamma, C \rangle + \lambda \sum_{i,j} \gamma_{i,j} ||x_i - y_j||^2$$

   Where $\lambda$ is a regularization parameter, and $x_i$ and $y_j$ are spatial coordinates.

3. **Multimodal Integration**: Incorporated RNA, ATAC, and protein data through a weighted cost function:

   $$c(x, y) = w_{RNA} \cdot c_{RNA}(x_{RNA}, y_{RNA}) + w_{ATAC} \cdot c_{ATAC}(x_{ATAC}, y_{ATAC}) + w_{prot} \cdot c_{prot}(x_{prot}, y_{prot})$$

For comprehensive details, tutorials, and examples, please refer to the [documentation](https://moscot.readthedocs.io/) or explore the [GitHub repository](https://github.com/theislab/moscot).
