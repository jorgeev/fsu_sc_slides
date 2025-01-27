---
title: "ViT: An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale"
author: "Alexey Dosovitskiy, Lucas Beyer, Alexander Kolesnikov, Dirk Weissenborn, Xiaohua Zhai, Thomas Unterthiner, Mostafa Dehghani, Matthias Minderer, Georg Heigold, Sylvain Gelly, Jakob Uszkoreit, Neil Houlsby"
date: "2020-12-06"
theme: metropolis
institute: "Florida State University (FSU)"
toc: false
footer: "Papers Club (Spring 2025)"
---

## Introduction

- The transformer fastly became the state-of-the-art architecture for Natural Language Processing (NLP) tasks.
- Limited usage in image recognition tasks.
  - Attention Mechanism was used to replace structures in CNNs.
- Vision Transformer (ViT) was not the first model to use transformer for CV tasks, but it was the first model flexible and scalable.

## Related Work

There were previous uses of transformer for CV tasks, but they were not scalable.

## Method

### Vision Transformer (ViT)

They tried to use transformers as RAW as possible to Image Classification tasks.

![Vision Transformer Architecture](./images/VIT_arch.png)

### Training data

- ImageNet-1k: 14M images from 21K classes. (Midium-sized dataset)
- JFT-300M: 303M images from 18K classes. (Large-sized dataset)

### Model Training

1. Split the images into patches.
2. Flatten the patches into a sequence of tokens.
3. Add positional embeddings to the tokens. (Notion of position is important for transformers)
4. Tran the model using supervised learning.

### Learning results

The medium-size model was underwhelming, the performance was on par or worse than the state-of-the-art CNNs.
The large-size model was able to outperform the state-of-the-art CNNs.

## Experiments

### Setup

### Comparison to SOTA

### Scalability

### Inspecting ViT

### Self-supervision

## Conclusion
