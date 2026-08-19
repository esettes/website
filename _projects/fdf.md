---
title: "FDF"
priority: 5
date: 2022-09-01
excerpt: "Representación gráfica de mapas de altura mediante proyección isométrica, transformaciones y rasterizado de líneas."
status: "Completado"
role: "Desarrollo gráfico y algoritmos"
category: "Gráficos y algoritmos"
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
## El proyecto

FDF transforma un archivo de alturas en una malla navegable. Cada número representa la
coordenada Z de un punto y el programa proyecta la escena sobre una ventana 2D.

## Implementación

- Lectura y validación del mapa de entrada.
- Algoritmo de Bresenham para rasterizar cada segmento.
- Proyección isométrica mediante transformaciones trigonométricas.
- Zoom, traslación, rotación y escalado de altura.
- Gradientes de color según profundidad y relieve.

## Resultado

El proyecto combina programación en C, gestión manual de memoria, matemáticas y un bucle
gráfico interactivo. Dentro del portfolio aporta una muestra visual del trabajo de bajo
nivel y de la capacidad para convertir datos en una representación explorable.
