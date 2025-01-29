---
title: "Vision Transformers (ViT)"
subtitle: "ViT: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (Dosovitskiy et al. 2020)"
author: "Jorge Eduardo Velasco Zavala"
date: "2025-01-29"
theme: metropolis
institute: "Florida State University (FSU)"
toc: false
header-includes:
  - \usepackage{biblatex}
  - \addbibresource{references.bib}
footer: "Papers Club (Spring 2025)"
---

## Introduction

- The transformer fastly became the state-of-the-art architecture for Natural Language Processing (NLP) tasks.
- Limited usage in image recognition tasks.
  - Attention Mechanism was used to replace structures in CNNs.
- Vision Transformer (ViT) was not the first model to use transformer for CV tasks, but it was the first model flexible and scalable.

### Main idea behind the paper

- Apply **Transformer** architecture as directly as possible to image classification tasks without relying on image-specific inductive biases like in CNNs.
- Test the capabilities of the **Vision Transformer** (ViT) against the state-of-the-art CNNs models.

## Motivations

- **Transformers'** attention mechanism was a success in NLP, but its potential in vision tasks was not fully explored.
- There were previous uses of transformer for CV tasks, but they were not scalable or an addition to CNNs.
- CNNs incorporate inductive biases like locality and translation equivariance, which help with smaller datasets.
- **Can Transformers perform better without these biases when given enough data?**

## ViT Architecture

- **Patch Embedding**: Extract patches from the image and embed them into a sequence of tokens.
- **Positional Encodings**: Add positional information to preserve the spatial structure of the image.
- **Transformer Encoder**: Apply the **transformer** to the sequence of tokens (patches).
- **Classification Head**: Add an MLP to classify the image.

## Vision Transformer (ViT)

They tried to use **transformers** to Image Classification tasks.

![Vision Transformer Architecture](./images/VIT_arch.png)

## Training a Vision Transformer

### Datasets

- In **Transformes** the large datasets critical for good performance.
  - ILSVRC-2012: 1.3M images from 1000 classes. (Small-sized dataset)
  - ImageNet-1k: 14M images from 21K classes. (Midium-sized dataset)
  - JFT-300M: 303M images from 18K classes. (Large-sized dataset)

### Training and Fine-tuning

- All the ViTs were trained using supervised learning.
- Fine-tuning or transfer learning was used to adapt the model to the target dataset.
- All models were trained using ADAM optimizer.

## Model Variants

![Model Variants](./images/vit_variants.png)

## ViT Results against state-of-the-art CNNs

![Classification Benchmark](./images/benchmarks.png)

## More benchmarks

![Classification Benchmark](./images/benchmarks2.png)

## Pre-training data requirements

![Data Requirements](./images/data_req.png)

## Pre-training findings

- Vision Transformers overfit more than ResNets with comparable computational cost on smaller datasets.
- This result reinforces the intuition that the **convolutional inductive bias is useful for smaller datasets**
- For larger ones, learning the relevant patterns directly from data is sufficient, even beneficial.
  - Better performance with of ViT pre-trained on the JFT-300M dataset.

## Positional Embeddings

They tested different approaces to enforce the notion of *position* in the image. Using 1D positional embeddings, 2D positional embeddings and relative positional embeddings.

![Positional Embeddings Performance](./images/position.png)

## Internal Representations

- The top principal components of Vision Transformers are more similar to those of CNNs.
  - Resembre plausible basis function for low dimensional structures in each patch.
- The model learns to encode distance or relative position within the image.
  - Patches in the same row or colum have similar embeddings.
- Self-attention allow the integration of global information in the image.
  - Most of the attention heads attent to large portions in the image in the deepst layers.
  - In shallow layers, the attention is more localized.

## ViT Internal Representations

![Inspecting ViT](./images/inspection.png)

## Attention Rollout

![Attention Rollout](./images/rollout.png)

## Posible self supervised pre-training

Another strength of the **Transformer** on NLP is the ability to perform **self-supervised pre-training**, the tested a *masked patch prediction* for self-supervision an they found that performed very well the mean of the 3bit color for the masked patches
They only report it performed quite well at this task but they didn't report the metrics beside it performed 4% behind the original ViT-B/16.

## Conclusions

- ViT don't introduce image-specific inductive biases. (Beside initial patch extraction)
- Archived the image processing as a sequence of tokens (patches) by a **Transformer encoder**.
  - In the same way as NLP tasks.
- Relatively cheap to train and learning transferable.
- Larger scale ViT possible and promising performance improvements.
- Promising results in self-supervised learning.
- Still need to extend the ViT to other CV tasks.
  - Segmentation, Detection, etc.

## References
