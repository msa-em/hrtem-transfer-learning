---
title: Effect of training dataset noise and structure
short_title: Noise and structure
numbering:
  enumerator: 9.%s
label : results_noise_structure
---

::: {figure}  #app:noise_widget
:placeholder:  ./figures/fig_noise.png
:name: fig_noise
Performance of U-Net models on CdSe nanoparticle datasets varying in electron dose after pretraining (left) and after transfer learning (right). Data are aggregated over all model freezing options; the median of model performance is taken per pair of electron doses.
:::


Neural network model performance, after only pretraining, is fairly sensitive to the noise distribution of the training data within the doses tested as shown in {ref}`fig_noise`. Models trained on low dose images are worse across the board, possibly due to the difficulty of the training data. After transfer learning, however, model performance in the transfer learning domain is fairly consistent regardless of the source of pretraining data, similar to the behavior across datasets differing in defocus. Performance after transfer learning seems to depend only on the signal-to-noise of the target dataset, indicating that our neural network models can be well adapted to changes in noise conditions by the use of transfer learning.

::: {figure} #app:structure_widget
:placeholder: ./figures/fig_structure.png
:name: fig_structure
Performance of U-Net models on nanoparticle varying in lattice structure (top) and nanoparticle size (bottom) after pretraining (left) and after transfer learning (right). Data are aggregated over all model freezing options. For the confusion matrices comparing structure classes, only small nanoparticle sizes are considered and the median of model performance is taken per pair of lattices.
:::

The dependence of segmentation performance on nanoparticle structure is a bit more complex than performance shifts due to shifts in imaging or noise conditions. As shown in {ref}`fig_structure`, our segmentation models tend to perform comparably well on nanoparticles which share similar crystal symmetries after the pretraining phase. Within a symmetry class, models trained on structures with lighter elements can perform slightly better both in- and out-of-distribution, but this is not completely consistent. Similar to the observed model behavior across the noise domain, after transfer learning, performance on a new nanoparticle structure mostly depends on the target domain structure. The size distribution of the nanoparticles has a weak effect on neural network performance, though, after only pretraining, model performance on the large nanoparticle datasets degraded slightly if the model was trained on small nanoparticles. Differences in performance were largely ironed out after transfer learning. 