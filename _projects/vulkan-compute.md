---
title: "Compute shaders con Vulkan"
priority: 6
date: 2023-04-01
excerpt: "Experimento de computación GPU que genera un fractal y compara el mismo trabajo ejecutado en CPU y mediante un compute shader."
status: "Experimento técnico"
role: "Implementación y documentación de aprendizaje"
category: "GPU y bajo nivel"
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
## Objetivo

Comprender el coste y el control explícito de Vulkan al ejecutar computación general en
GPU, siguiendo una inicialización completa del dispositivo y del pipeline de compute.

## Experimento

El programa genera un fractal de 1000 por 1000 píxeles mediante dos implementaciones
equivalentes. En la ejecución documentada en el repositorio, la CPU necesitó 285 ms y la
GPU 4 ms. El resultado no pretende ser un benchmark universal, sino una demostración
práctica del paralelismo disponible para este tipo de carga.

## Aprendizaje

El proyecto parte de un curso de computación GPU con Vulkan y documenta el proceso de
inicialización, selección de memoria, creación de buffers, descriptores y sincronización.
Se presenta como experimento formativo, diferenciándolo de los proyectos originales del
portfolio.
