---
title: Effect of training dataset imaging conditions on model performance
short_title: Imaging conditions
numbering:
  enumerator: 7.%s
label : results_data
---


:::{figure} #app:domain_widget
:placeholder: ./figures/fig_dataset_perf.png
:name: fig_dataset
Dependence of neural network model performance in the transfer domain on the pretraining data domain after just pretraining (top) and after transfer learning (bottom). Data are aggregated over all hyperparameter configurations; the median of the model performance is taken per defocus pair.
:::

:::{figure} #app:baseline_widget
:placeholder: ./figures/fig_baseline.png
:name: fig_baseline
Baseline performance comparison of transfer learning training of U-Net models from -10nm defocus to +5nm defocus (dashed lines), against single training phase training using a dataset mixture (solid lines) of the two defoci at various dataset compositions. Transfer learning performance is measured against the target dataset (5nm) only. All training phases used a training dataset size of 512 images before augmentation and were optimized for 10 epochs with the Adam optimizer. For the single training phase models, a learning rate of 1e-4 was used; for the transfer learned models, the pretraining phase used a learning rate of 1e-4, and the transfer learning phase used a learning rate of 1e-5. Performance is measured as mean performance of three models.
:::

Naturally, beyond training hyperparameters, the content of the training datasets has the largest impact on model performance. Within the context of transfer learning, it is important to try to understand the relationship between pretraining datasets to the transfer learning domain(s) of interest and any impacts of such relationships on model performance. In our study, it seems that the source of the pretraining data has only a minor impact on model performance, possibly due to fairly constrained data domain. As shown in {ref}`fig_dataset`, bottom, model performance is fairly consistent in the transfer learning domain after transfer learning has been performed regardless of the pretraining data, even though after only pretraining, there is notable performance dependence on the pretraining domain. It is useful, also, to consider an idealized comparison baseline to contextualize the success (or lack thereof) of transfer learning. In {ref}`fig_baseline`, we showcase results from a series of models trained in just a single stage utilizing a mixture of two datasets. For a mixture of -10nm and 5nm defocus data, with 5nm data serving as the transfer domain, performance after transfer learning and when utilizing a single training phase seem comparable for similar amounts of overall 5nm data. However, though this seems more strongly dependent on the domains of interest, as for some defocus combinations the two approaches have more divergent behavior. Importantly, in many scenarios, transfer learning can readily provide performance comparable to training entirely with data in the transfer domain, even with a small dataset. 

There can also exist fundamental asymmetries in the relative information between two ostensibly similar data domains, resulting in a greater utility in using one dataset to pretrain over the other. In our experiments, this is most obvious with the 'in-focus' dataset, which is the hardest for our models to successfully segment; yet, models trained on the in-focus data can achieve better performance out-of-distribution and are much more successful transfer learning to a new focal point than model trained on other focal points are to the in-focus data. This suggests that using more general and difficult training datasets for pretraining can possibly provide a distinct advantage in transfer learning workflows.