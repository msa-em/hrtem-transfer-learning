---
title: Neural network architecture and training procedure
short_title: Training procedure
numbering: 
  enumerator: 3.%s
label : methods_training
---

:::{figure} ./figures/fig_nn.png
---
name: fig_arch
---
Architecture of U-Net neural network with ResNet backbone. Initial processing block consists a convolutional layer, a batch norm and activation layer, and a max pooling layer. The encoder half of the model encompasses the initial block and the downsampling blocks, while the decoder half encompasses the upsampling blocks.
:::

For our neural network architecture, we use a standard U-Net model following previous work [@rangeldacostaRobustSyntheticData2024; @ronnebergerUNetConvolutionalNetworks2015] and shown in {ref}`fig_arch`; in total, each network had about 14 million trainable parameters. Using PyTorch [@pytorch] for model training and a analysis, we optimize U-Net models in two fixed length stages of 10 epochs each, corresponding to the pretraining and transfer learning stages. In the pretraining stage, we utilized a training dataset size of 512 images before dihedral augmentation and in the transfer learning stage, we variably trained models with 64, 128, 256, and 512 images, using a fixed minibatch size of 16 images in both stages. We optimize model parameters with the Adam optimizer [@kingma2017adammethodstochasticoptimization] against the cross entropy loss of their predictions with learning rates of 1e-3 and 1e-4 during pretraining and 1e-4 and 1e-5 during transfer learning and a multiplicative learning rate decay factor of 0.99 per epoch. We also test model weight freezing approaches, making either all weights trainable or freezing parameters within the decoder or encoder portions of the U-Net model. For each hyperparameter/dataset configuration, we train 3 randomly initialized models. In our visualizations and analysis, we adjust measured losses by an offset of 0.3133, which is the minimum achievable cross entropy loss for a two-class segmentation or classification task. 

Including all model variations across training hyperparameter conditions, we trained 2400 unique model configurations for a total of 7200 total trained models on the CdSe defocus dataset. We reduce the training conditions we test for the noise varying and structure varying datasets, adjusting only the weight freezing protocols and fixing learning rates to 1e-4 during pretraining and 1e-5 during transfer learning and the transfer dataset size to 128, for an additional 180 and 2754 models, respectively. The training of the models for the noise and structure varying series utilized automated mixed-precision training [@micikevicius2018mixedprecisiontraining], which downcasts certain computations to half-precision to reduce training memory costs and time, and GPU power capping to 250W and limits the total power draw of GPUs (and thus energy consumption) at a small increase in training time [@nersc_GPU_power].

Lastly  we ran a baseline comparison series of neural networks, trained only in a single pretraining phase using mixtures of 128:384, 256:256, and 384:128 images for each of unique dataset pairs in the defocus model series. We use both pretraining learning rates of 1e-3 and 1e-4. The baseline comparison series comprises an additional 720 models.