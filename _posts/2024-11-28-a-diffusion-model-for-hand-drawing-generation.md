---
title: A Conditional Diffusion Model for Hand-drawing Generation
date: 2024-11-28 14:00:00 +/-0000
categories: [Course, Project]
tags: [course project, diffusion]     # TAG names should always be lowercase
author: fishyi
---

This homework implements an efficient CFG diffusion model that generates hand-drawing images conditioned on 12 class labels with only 6,586,369 model parameters and 100 diffusion steps.

# Introduction

Given a hand-drawing image dataset containing the following categories: `"airplane", "bus", "car", "fish", "guitar", "laptop", "pizza", "sea turtle", "star", "t-shirt", "The Eiffel Tower", "yoga"`, we aim to generate new hand-drawing images conditioned on these categories.

We adopt u-net based diffusion model to generate images. For conditioning, we use the Classifier-free Guidance technique.

# Results

The generated results are shown below:

![generated results](/assets/post/2024-11-28-a-diffusion-model-for-hand-drawing-generation/guidance0.5.png)
_Guidance Scale = 0.5_
![generated results](/assets/post/2024-11-28-a-diffusion-model-for-hand-drawing-generation/guidance2.0.png)
_Guidance Scale = 2.0_
![generated results](/assets/post/2024-11-28-a-diffusion-model-for-hand-drawing-generation/guidance5.0.png)
_Guidance Scale = 5.0_



For more implementation details, please refer to the [github page of this project](https://github.com/F1shYi/diffusion12/).
