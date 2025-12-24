---
title: Generalization measures
short_title: Generalization measures
numbering: 
  enumerator: 4.%s
label : methods_measures
---

In supervised learning, we use the validation loss—more formally known as the generalization gap in empirical risk minimization settings—as our working metric for measuring in-distribution generalization $G_{ID}$. For a parameterized model $f_\theta: X \rightarrow Y$ optimized against a loss function $\mathcal{L}$,

:::{math}
:label: eq_giid
G_{\scriptscriptstyle\text{ID}, \mathcal{X}} (f_\theta) = \mathcal{L} \left(f(X), Y \right) - \underset{S \sim \mathcal{X}}{\mathbb{E}}\left[ \mathcal{L} \left( f (X), Y \right) \right]
:::

where $(X, Y)$ are the data and supervision labels (i.e., micrographs and segmentation masks) drawn from an underlying distribution $\mathcal{X}$ and $S$ is the finite sample of data used to optimize the model $f_\theta$. The loss $\mathcal{L} \left(f_\theta(X), Y \right)$ represents the performance of the model over the entire domain $\mathcal{X}$, but in practice, we approximate this loss using a second finite dataset—deemed the validation dataset—which should be drawn independently and identically distributed to the training sample $S$. During model training, we optimize model weights $\theta$ against the training loss $\mathbb{E}_S\left[ \mathcal{L} \left( f_\theta (X), Y \right) \right]$; commonly, final weights for a model are instead selected to correspond to parameters which minimize $G_{\scriptscriptstyle\text{ID}}(f_\theta)$.



Using the shorthand $\mathcal{L}_{\mathcal{X}}(f) =  \mathcal{L} \left(f(X), Y \right)$, we can analogously define an out-of-distribution generalization metric as 

:::{math}
:label: eq_good
G_{\scriptscriptstyle\text{OOD}, \mathcal{X} \rightarrow \mathcal{X}'} (f) = \mathcal{L}_{\mathcal{X'}}(f) - \mathcal{L}_{\mathcal{X}}(f)
:::

where $\mathcal{X}$ is the training distribution of $f$ and $\mathcal{X'}$ is a new distribution of data which differs from $\mathcal{X}$, i.e., under some measure, $\mathcal{X} \neq \mathcal{X'}$. Both terms in Eq. @eq_good must be approximated with validation datasets in practice. We note, also, that Eq. @eq_good is not always nonnegative, unlike Eq. @eq_giid (which, in theory, should be): one can imagine a scenario in which a model improves out of distribution. 