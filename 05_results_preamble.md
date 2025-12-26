---
title: Preamble and interactive data interpretation
short_title: Preamble
numbering:
  enumerator: 5.%s
label : results_preamble
---


In general, we will discuss results which are aggregated across all trained models and training settings to help clarify our presentation. For example, when discussing the effect of freezing a UNet's encoder weights, we consider the response of all models with frozen encoder weights regardless of the amount of data, learning rates, or which datasets were used for training. Such aggregation hides much of the nuance and complexity of designing machine learning protocols and is not always appropriate, due to possible interrelated and confounding effects of these decisions on model performance; our static figures will visualize these aggregate results. We invite and encourage the reader to further explore the interrelated effects between transfer learning protocol decisions via the interactive visualization, which is designed to let one query and visualize any particular subset of our trained model database. For example, if you are curious about whether or not weight freezing affects model generalization to out-of-distribution data (shown in {ref}`fig_gen`), you can adjust the visualization to only include training results from models trained with frozen encoders.

When exploring how performance varies across a training option, we will also sometimes reduce performance down to single numbers, i.e., by using the median model performance to represent a typical possible outcome of a certain training protocol. More extreme results such as the worst case (maximum loss) or best case (minimum loss) model outcomes, which might have larger influences on how one might design their ML workflows, may be more useful or interesting to consider instead. If data reduction is performed in the visualization of a figure, the choice of reduction will also be flexible via the interactive visualization via the 'Reduction Mode' selection. In the main text, unless otherwise specified, we will discuss median model performances.