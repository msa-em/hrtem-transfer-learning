---
title: Simulated dataset generation
short_title: Datasets
numbering: 
  enumerator: 2.%s
label : methods_datasets
---

:::{figure} #app:example_image_widget
:placeholder: ./figures/example_placeholder.png
:name:fig_data
Example training images from datasets used in this study. Scale bar is 2nm.
:::


:::{table} Lattice structures used for nanoparticle generation.
:label: tab_structures
| Structure | Space Group | Lattice parameters ( $\text{\AA}$ ) |
| - | -: | -: |
| ZnS  | 186 | 3.8227 (a), 6.2607 (c) |
| CdSe | 186 | 4.2985 (a), 7.0152 (c) |
| Cu  | 225 | 3.6157|
| Ag  | 225 | 4.0782|
| C | 227 | 3.5673 |
| Si | 227 | 5.430 |
| Fe3O4 | 227 | 8.394|
| Co3O4 | 227 | 8.065 |
| Fe | 229 | 2.866 |
:::


Simulated datasets were generated using Construction Zone [@rangeldacostaRobustSyntheticData2024] for structure sampling and generation, and a combination of the Prismatic [@rangeldacostaPrismatic20Simulation2021] and abTEM [@abtem] software packages for image simulation. HRTEM simulation was performed using the multislice algorithm, with an accelerating voltage of 300kV, a real space sampling of 0.1 $\text{\AA}$ , and 8 frozen phonons. Images were then downsampled to a resolution 0.2 $\text{\AA}$ , after which defocus and electron dosage effects were applied; for all images, we applied chromatic aberration effects corresponding to focal spread of 10 $\text{\AA}$.

For each structure, we simulate the full structure and the nanoparticles alone in vacuum. We generate ground-truth segmentation labels using the nanoparticle-in-vacuum simulation by applying a phase threshold against the exit wave, which generates masks that are consistent across imaging conditions and apply a small Gaussian blurring kernel to smoothen the segmentation label. We visually optimized the threshold to $\pi/16$ for all structures, and the Gaussian kernel sizes to 1 $\text{\AA}$ , for the C, Fe, and Co$_3$O$_4$ structures, and 1.6 $\text{\AA}$ for all other structures. We calibrate zero defocus per structure to the minimum contrast condition of the nanoparticles in vacuum, and determined heuristically with a two-stage grid search of defocus values with grid samplings of 1 and 0.1 $\text{\AA}$  and using the variance of the image intensity as a proxy for image contrast. Electron doseage effects are applied via sampling of a Poisson distribution after scaling pixel values by the effective dose. Before training, input images are standardized to a mean of 0 and variance of 1, per image.

Three dataset series were constructed in total: one varying in image defocus, one varying in electron doseage, and one varying in the nanoparticle structures. Across all datasets, nanoparticles were placed atop 12.8nm by 12.8nm amorphous carbon substrates between 2nm and 8nm thick. For the defocus dataset, we generate a series of CdSe nanoparticle structures. Each structure contains between one and five spherical wurtzite CdSe nanoparticles ranging between 3-5 nm in diameter, with each nanoparticle containing up to two stacking faults and separated from other nanoparticles by a distance of at least 1nm. Eleven defocus conditions were sampled post-simulation for each image from -25 to +25nm in steps of 5nm with a standard deviation of 1.5nm. The five defocus datasets between -10nm and +10nm defocus were used for model pretraining and all were used for transfer learning,resulting in 50 total possible dataset combinations (excluding repeat defoci) across both training stages. For the defocus datasets, we applied an electron doseage of 400 $e-\text{per \AA}^{-2}$. For the noise datasets, we utilize the same CdSe nanoparticle structures and simulations, a fixed defocus of -10nm with a standard deviation of 1.5nm, and electron doseages of 30, 75, 150, 300, and 600 $e-\text{per \AA}^{-2}$. For the structure varying datasets, we generate 18 different nanoparticle structure distributions corresponding to 2 size distributions and 9 crystal structures varying in chemistry and lattice symmetry (c.f. {ref}`tab_structures`). Nanoparticle sizes are uniformly distributed with radii between 1 and 2nm (small) or between 2.5 and 3.5nm (large), with between 1 and 5 nanoparticles per structure, placed atop the substrate as previously described for the defocus dataset. For the imaging conditions, we use a fixed defocus of -10nm with a standard deviation of 1.5nm and apply an electron doseage of 300 $e-\text{per \AA}^{-2}$. 
