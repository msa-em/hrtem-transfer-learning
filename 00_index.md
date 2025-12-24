---
title: Strategies for effective transfer learning for HRTEM analysis with neural networks
short_title: Transer Learning for HRTEM Segmentation
numbering:
  heading_2: false
---

+++ {"part": "abstract"} 

Transfer learning provides a practical opportunity to adapt machine learning models to new domains by retraining models on a new, typically smaller set of data. This technique is especially useful for supervised learning problems in electron microscopy, where high-quality, labeled experimental data are scarce and experimental conditions can change significantly across experiments. Using simulated benchmark datasets, we investigate a series of transfer learning protocols for developing segmentation models for locating nanoparticles in high-resolution transmission electron microscopy (HRTEM) data. We train over 10,500 neural networks and evaluate model performance and out-of-distribution generalization capabilities after both pretraining and transfer learning phases, covering shifts in imaging conditions, noise conditions, and structural distributions. Via our high-throughput data generation and model training approach, we demonstrate that transfer learning can be an effective strategy to tackle domain shifts in machine learning problems for HRTEM and that transfer learning can be beneficial for model generalization. Lastly, we provide some practical training recommendations for adopting transfer learning protocols into machine learning development pipelines.
+++


+++{"part":"epigraph"}
:::{warning} Pre-print
This article has not yet been peer-reviewed.  
:::

+++

+++ {"part": "acknowledgements"} 

This material is based upon work supported by the U.S. Department of Energy, Office of Science, Office of Advanced Scientific Computing Research, Department of Energy Computational Science Graduate Fellowship under Award Number DE-SC0021110.  Work at the Molecular Foundry was supported by the Office of Science, Office of Basic Energy Sciences, of the U.S. Department of Energy under Contract No. DE-AC02-05CH11231. This research used resources of the National Energy Research Scientific Computing Center (NERSC),  a Department of Energy User Facility using NERSC award BES-ERCAP 32753. This work was prepared in partial fulfillment of the requirements of the FUSE Program, and is supported by a partnership between the Molecular Foundry and Workforce Development & Education at Berkeley Lab.
+++

+++ {"part": "competing interests"} 
## Competing Interests

The authors declare no competing interests.
+++
