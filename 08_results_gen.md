---
title: Effect of training dataset imaging conditions on model OOD generalization
short_title: Model OOD generalization
numbering:
  enumerator: 8.%s
label : results_gen
---


:::{figure} #app:gen_widget
:placeholder: ./figures/fig_generalization.png
:name: fig_gen
Out-of-distribution (OOD) generalization capabilities of neural networks throughout the transfer learning protocol. (left, top) Standard-deviation of loss on defocus domains before and after transfer learning; larger is worse. (left, bottom) Shift in standard deviation of loss before and after transfer learning; more positive is worse. (right) Performance of neural network on all OOD domains before and after transfer learning (left and right bars, respectively). Color of bars indicate standard deviation of loss before transfer learning (left set) and shift of standard deviation after transfer learning (right set); markers on confusion matrices locate the particular defocus pair chosen for each bar plot. Loss is measured as the median network loss as aggregated over all hyperparameter conditions; standard deviation of performance excludes the 0nm (in-focus) dataset.
:::


While performance in the transfer domain across image conditions seems to have a weak dependence on the choice of the pretraining dataset, the out-of-distribution (OOD) generalization behavior of our U-Net models has a relatively strong dependence on the choice of both pretraining and transfer learning datasets. In {ref}`fig_gen`, we visualize the OOD performance of our models before and after training, as measured by the standard deviation of the model loss across all defocus datasets, as well as the relative shift in generalization between the two stages. Across the board, transfer learning, while offering good target domain performance, does not necessarily improve model OOD. In fact, transfer learning can make the OOD generalization capability of a model noticeably worse, but it is not clear when this might occur. While this asymmetry is perhaps obvious in some scenarios, such as the asymmetry between simulated and experimental data, it can be less obvious when comparing datasets that seem semantically similar, such as data taken across microscope sessions or across similarly prepared samples. In general, the models trained on positive defoci have worse generalization than other models, but can significantly improve their generalization (c.f. {ref}`fig_gen`, right) with the right choice of transfer learning domain, to the point of performing almost equally well across all our datasets. In this analysis, we exclude the performance on the 0nm 'in-focus' dataset from the OOD generalization measure, as it is the hardest dataset and tends to be an outlier in performance. However, we note that models trained with the 0nm defocus dataset have some of the best OOD generalization behavior, performing significantly better out-of-distribution than on their own training data, which is another reflection of the possible asymmetries which may be inherent to our datasets.