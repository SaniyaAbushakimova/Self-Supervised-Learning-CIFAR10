# Self-Supervised-Learning-CIFAR10

Project completed on April 3, 2025.

## Project Overview

This project explores self-supervised learning through a rotation prediction task, inspired by the work of Gidaris et al. (2018) titled *“Unsupervised Representation Learning by Predicting Image Rotations.”* The goal is to learn meaningful image representations without using class labels and to transfer these representations to a supervised image classification task on the CIFAR-10 dataset.

A ResNet18 model is first pre-trained on a rotation classification task, where images are randomly rotated by 0°, 90°, 180°, or 270°, and the model learns to predict the applied rotation. The core idea is that, in order to solve the rotation task, the network must understand object structures, orientation, and context — it cannot recognize a “cat upside down” without implicitly knowing what a cat looks like. This encourages the network to learn high-level semantic features (like edges, textures, and object parts) that are useful for other tasks, such as object classification. Once the model has learned these features, they can be transferred and fine-tuned on a supervised classification task, improving performance — especially when labeled data is limited.

The project also explores fine-tuning the pre-trained model for CIFAR-10 classification, training a more advanced architecture (EfficientNetV2-L), and comparing performance under both full supervision and semi-supervised settings. These experiments demonstrate the value of self-supervised learning as a strong initialization strategy.

## What This Project Includes
**1. Rotation Prediction (Self-Supervised Pretraining):** ResNet18 is trained to classify the rotation angle of input images as a pretext task to learn semantic representations. 

**2. Fine-Tuning Last Layers:** The final block and linear classification layer of the pre-trained ResNet18 are fine-tuned for CIFAR-10 image classification. 

**3. Full Network Fine-Tuning:** The entire pre-trained model is fine-tuned and compared to a model trained from scratch.

**4. Advanced Architecture Training:** EfficientNetV2-L is trained both from scratch and using pre-trained rotation weights to push classification accuracy further. 

**5. Semi-Supervised vs Supervised Comparison:** A comparative experiment recreating the Gidaris et al. paper’s Figure 5b shows the advantage of self-supervised learning when labeled data is limited.

## Results Summary
<img width="625" alt="Task Description" src="https://github.com/user-attachments/assets/9b1245bf-360e-4a7d-b411-8bd26c3e5121" />

In semi-supervised settings, models initialized with rotation-pretrained weights outperformed fully supervised models when trained on fewer than 1000 labeled images per class.

## Repository Contents
* `self_supervised_cifar10.ipynb` -- Jupyter notebook containing all training, fine-tuning, and evaluation steps using PyTorch.
* `Report.pdf` – summary of experimental results and observations.
