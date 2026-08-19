---
title: "GPU computing with Vulkan"
priority: 7
date: 2023-04-01
excerpt: "GPU computing experiment that generates a fractal and compares the same workload on a CPU and a compute shader."
status: "Technical experiment"
role: "Implementation and learning documentation"
category: "GPU and low-level programming"
code: "GPU"
stack:
  - C++
  - Vulkan
  - GLSL
  - GPU computing
repo_url: "https://github.com/esettes/compute_shader_vulkan"
demo_url: ""
cover: "/assets/images/projects/Compute shaders con Vulkan.png"
---
## Goal

Understand Vulkan's cost and explicit control model when running general-purpose GPU
computing, including complete device and compute pipeline initialization.

## Experiment

The program generates a 1000 by 1000 pixel fractal through two equivalent implementations.
In the run documented in the repository, the CPU took 285 ms and the GPU took 4 ms. This
result is not presented as a universal benchmark, but as a practical demonstration of the
parallelism available for this workload.

## What I learned

The project follows a Vulkan GPU computing course and documents initialization, memory
selection, buffer creation, descriptors, and synchronization. It is presented as a learning
experiment and kept distinct from the portfolio's original projects.
