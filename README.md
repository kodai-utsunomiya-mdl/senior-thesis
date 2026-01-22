# Elementary Analysis of Learning Dynamics in Deep Neural Networks

This repository contains the resources for my Bachelor's Thesis, submitted in February 2025.

**Author:** Kodai Utsunomiya

## Abstract

Deep neural networks often employ architectures where the number of neurons (width) varies significantly across layers (e.g., bottleneck structures). However, existing theories on learning dynamics in the infinite-width limit, such as **Neural Tangent Kernel (NTK)** and **Maximal Update Parametrization ($\mu$P)**, typically assume that all hidden layer widths scale at the same order (i.e., $n_l = \Theta(n)$ for all $l$).

This thesis investigates the learning dynamics when intermediate layer widths increase at different orders (e.g., $n_l = \Theta(n)$ vs $n_k = \Theta(n^r)$).

**Key Contributions:**
1.  **Theoretical Analysis:** We derive that for stable learning—where parameter updates contribute to loss reduction without vanishing or exploding—the update magnitude is theoretically constrained by the **minimum layer width** ($n_{\min}$) in the network.
2.  **Dynamic Parametrization (DP):** Based on this insight, we propose a new parameterization method, *Dynamic Parametrization*, which explicitly adjusts initialization and learning rates based on $n_{\min}$. This ensures stable feature learning even in highly asymmetric bottleneck architectures.
3.  **Experimental Verification:** Experiments on CIFAR-10 demonstrate that DP outperforms **Spectral Parametrization** (Yang et al., 2023) in terms of training stability and generalization performance when bottleneck structures are emphasized.

## Contents

* `senior-thesis.pdf`: The full thesis document (in Japanese).
* `presentation-slide.pdf`: Presentation slides.
* `notebooks/`: Minimal scripts organized to be executable on Google Colab for reproducing the experimental results.

## Experiments & Reproduction

The following Jupyter notebooks contain the minimal code required to reproduce the figures in the thesis. Direct links to run them on Google Colab are provided below.

### 1. Optimization Conditions (Figure 3.2)
Verifying the optimization condition $|\langle \nabla_{\tilde{h}} \mathcal{L}, \Delta \tilde{h} \rangle| = \Theta(1)$ under **Spectral Parametrization**. The results show that this condition is violated when layer widths scale at different ratios ("Dynamic Ratio" setting).
* [**Open in Colab (Figure 3.2)**](https://colab.research.google.com/drive/19aHe4t-7xe6Vl3GjsScgC9xtdtYCXUaM?usp=sharing)

### 2. Validation of Dynamic Parametrization (Figure 3.3)
Verifying that the proposed **Dynamic Parametrization (DP)** satisfies the optimization condition $|\langle \nabla_{\tilde{h}} \mathcal{L}, \Delta \tilde{h} \rangle| = \Theta(1)$ even in varying-width settings, ensuring stable optimization.
* [**Open in Colab (Figure 3.3)**](https://colab.research.google.com/drive/1LwBRXZqHkg31K297iY5BwXY9pC3F_moB?usp=sharing)

### 3. Performance Comparison (Figures 3.4 - 3.7)
Comparing the Training and Test Loss of DP vs. Spectral Parametrization on CIFAR-10 subsets (binary classification tasks). DP demonstrates faster convergence and better generalization in bottleneck architectures.
* [**Open in Colab (Figures 3.4 - 3.7)**](https://colab.research.google.com/drive/1tnmcAArIlS6J8N8G_ljXIAy0k9R4Xaa0?usp=sharing)

## References

1.  Greg Yang and Edward J. Hu. **Tensor Programs IV: Feature Learning in Infinite-Width Neural Networks**. *International Conference on Machine Learning (ICML)*, 2021. [[arXiv]](https://arxiv.org/abs/2011.14522)
2.  Greg Yang, James B. Simon, and Jeremy Bernstein. **A Spectral Condition for Feature Learning**. *arXiv preprint arXiv:2310.17813*, 2023. [[arXiv]](https://arxiv.org/abs/2310.17813)
