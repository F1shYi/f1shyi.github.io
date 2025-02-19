---
title: 在DDPM的去噪过程中进行条件引导
date: 2025-02-19 14:00:00 +/-0000
categories: [Paper, Digest]
tags: [paper digest, diffusion, conditioning]     # TAG names should always be lowercase
author: fishyi
description: 本文讨论了在DDPM去噪过程中进行条件引导的一些方法
math: true
---

在DDPM的去噪过程中，如果不加以引导，其随机性会导致一个巨大的隐空间。而如果我们用外部条件去引导，就可以在这个巨大的隐空间中找到一个与外部条件在某种意义上相符合的子空间（一般是在语义上与外部条件相符合）。

## ILVR

[ILVR](https://arxiv.org/abs/2108.02938)的想法是，给定reference image $$y$$，我们想要生成的图片$$x_0$$在语义上与$$y$$接近。其做法为在去噪的第$$t$$步，给条件加噪得到$$y_t$$，按理说$$x_t$$与$$y_t$$应当有相似的语义。于是我们用$$x_t-\phi(x_t)+\phi(y_t)$$来替代原本的$$x_t$$进行去噪，其中$$\phi$$是一个语义提取器，提取我们关心的语义，该公式的含义为去掉$$x_t$$的语义并替换为$$y_t$$的语义，从而实现在隐空间中朝着条件的方向走一步。

在原论文里$$\phi$$实现为一个低通滤波器，提取了色块，低频特征等语义。

## Sketch-Guided Text-to-Image Diffusion Models

[Sketch-Guided Text-to-Image Diffusion Models](https://arxiv.org/abs/2211.13752)实现了让文生图的生成结果符合sketch的线条。其做法为，固定UNet $$U$$，对去噪步$$z_t$$，取$$U(z_t)$$的一些隐藏激活层作为特征，并根据这个特征训练一个edge predictor。edge predictor训练好后，在inference的过程中，用edge predictor的结果和真实的edge guidance之间的距离作为损失，优化$$z_t$$使得其边缘靠近给定的edge guidance image.

## Latent Aligners

[Seeing-and-Hearing](https://arxiv.org/pdf/2402.17723)的想法类似，但做法不同，它并不是将条件也加噪，然后让$$x_t$$去靠近$$y_t$$；它是先直接将$$x_t$$一步到位地解码成$$x_0$$，并计算$$x_0$$与$$y$$之间的距离$$l(x_0,y)$$，然后优化$$l(x_0,y)$$，更新$$x_t$$使得距离变小。这个方法的好处是距离函数$$l$$的选择可以是基于预训练好的编码器的，甚至可以是跨模态的编码器，在一个shared embedding space中计算距离。

