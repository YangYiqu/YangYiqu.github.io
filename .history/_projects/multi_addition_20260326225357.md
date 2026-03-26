---
title: "Making Arithmetic Transformers Generalizable and Interpretable"
excerpt: "

- Improving Length Generalization in Transformer-based Algorithmic Tasks: Systematically investigated positional encoding and carry representation strategies, proposing a 2D positional encoding with explicit carry tokens. Enabled small models trained on up to 10-digit numbers to generalize to nearly 200-digit inputs.

- Dual-Dimension Generalization for Multi-Operand Computation: Designed a computation framework with scratchpad reasoning and 3D positional encoding (operand–digit–region), enabling simultaneous generalization over number length and operand count. Achieved 79% sequence accuracy at a challenging 40×40 scale.

- Mechanistic Analysis of Computation Structure: Leveraged attention pattern analysis and Tuned Lens probing to reveal that addition is completed in early layers with localized carry modeling, providing an explanation for improved generalization.
<br/><img src='/images/pos_embedding.png'>"

collection: projects
---

- [Download Making_Arithmetic Transformers_Generalizable_and_Interpretable.pdf here](http://yangyiqu.github.io/files/DL_Report___Addition_Transformer (2).pdf)


