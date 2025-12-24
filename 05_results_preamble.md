---
title: Preamble
numbering:
  enumerator: 5.%s
label : results_preamble
---

We begin our survey on transfer learning protocols by looking at the primary high-level constraints and decisions made in the transfer learning workflow: the amount of data available in the transfer domain, whether or not the whole model is re-trained, and optimization hyperparameters. 

In general, we discuss aggregate results across all trained models and training settings to help clarify our presentation. For example, when discussing the effect of freezing a UNet's encoder weights, we consider the response of all models with frozen encoder weights regardless of the amount of data, learning rates, or which datasets were used for training. Such aggregation hides much of the nuance and complexity of designing machine learning protocols and is not always appropriate, due to interrelated and confounding effects of these decisions on model performance; our static figures will visualize these aggregate results. We invite and encourage the reader to further explore the interrelated effects between transfer learning protocol decisions via the interactive visualization which will let one query and visualize any particular subset of our trained model database. 

When exploring how performance varies across a training option, we will also sometimes reduce performance down to single numbers, i.e., by using the median model performance to represent a typical possible outcome of a certain training protocol. More extreme results such as the worst case (maximum loss) or best case (minimum loss) model outcomes, which might have larger influences on how one might design their ML workflows, may be more useful or interesting to consider instead. If data reduction is performed in the visualization of a figure, the choice of reduction will also be flexible via the interactive visualization. In the main text, unless otherwise specified, we will discuss median model performances.