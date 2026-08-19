---
title: "FDF"
priority: 6
date: 2022-09-01
excerpt: "Graphical rendering of height maps using isometric projection, transformations, and line rasterization."
status: "Completed"
role: "Graphics development and algorithms"
category: "Graphics and algorithms"
code: "3D"
stack:
  - C
  - MLX42
  - Bresenham
  - Isometric projection
repo_url: "https://github.com/esettes/FDF"
demo_url: ""
cover: "/assets/images/projects/FDF.png"
---
## The project

FDF transforms a height map file into a navigable mesh. Each number represents the Z
coordinate of a point, and the program projects the scene onto a 2D window.

## Implementation

- Input map parsing and validation.
- Bresenham's algorithm to rasterize each segment.
- Isometric projection through trigonometric transformations.
- Zoom, translation, rotation, and height scaling.
- Color gradients based on depth and elevation.

## Result

The project combines C programming, manual memory management, mathematics, and an
interactive graphics loop. It provides a visual example of low-level work and of turning
data into an explorable representation.
