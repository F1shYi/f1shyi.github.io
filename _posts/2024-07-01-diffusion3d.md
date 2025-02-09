---
title: A Simple Diffusion Model for 3D Shape(Pointcloud) Generation
date: 2024-07-01 14:00:00 +/-0000
categories: [Course, Project]
tags: [course project, diffusion, generative model]     # TAG names should always be lowercase
author: fishyi
---

This homework implements a simple, unconditional diffusion model for 3D shape generation.

# Introduction

We adopt PointTransformer to model pointclouds and predict the noise added. We choose three catogories of 3D shapes: airplanes, chairs and tables for training and generation.

# Results

The generated results are shown below:

![generated results](/assets/post/diffusion3d/airplane.png)
![generated results](/assets/post/diffusion3d/airplane_i_0.gif)
_Generated Airplane and Generation Process_

![generated results](/assets/post/diffusion3d/chair.png)
![generated results](/assets/post/diffusion3d/chair_i_0.gif)
_Generated Chair and Generation Process_

![generated results](/assets/post/diffusion3d/table.png)
![generated results](/assets/post/diffusion3d/table_i_0.gif)
_Generated Table and Generation Process_


For more implementation details, please refer to the [github page of this project](https://github.com/F1shYi/Diffusion/).
