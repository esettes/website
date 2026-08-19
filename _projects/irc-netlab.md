---
title: "irc-netlab"
priority: 2
date: 2026-08-03
excerpt: "Laboratorio reproducible en Python para iniciar, observar, probar y limpiar servicios IRC de forma automatizada."
status: "Fase inicial · En desarrollo"
role: "Requisitos, arquitectura, implementación y QA"
category: "Automatización y testing"
code: "QA"
stack:
  - Python 3.12
  - pytest
  - Ruff
  - Networking
  - CI
repo_url: "https://github.com/esettes/irc-netlab"
demo_url: ""
cover: "/assets/images/projects/irc-netlab.png"
---
## Objetivo

Probar un servidor de red de forma fiable requiere más que enviar comandos: hay que
controlar su ciclo de vida, saber cuándo está preparado, conservar evidencias y limpiar
todos los recursos incluso cuando una prueba falla.

`irc-netlab` nace como un laboratorio autónomo para ejecutar ese ciclo de forma
reproducible:

```text
validar -> iniciar -> esperar disponibilidad -> probar -> detener -> limpiar
```

## Principios de arquitectura

- El laboratorio puede funcionar sin un orquestador externo.
- Expone capacidades mediante contratos públicos y documentados.
- No depende de futuros laboratorios HTTP, TCP, DNS o WebSocket.
- Cada fase debe devolver resultados estructurados y evidencia útil para diagnóstico.
- La limpieza forma parte del resultado, no es una tarea secundaria.

## Base técnica

El proyecto utiliza Python 3.12, estructura `src`, CLI instalable, tests unitarios y de
integración, Ruff, construcción de wheel y decisiones de arquitectura documentadas.

## Estado honesto

La primera fase proporciona la base ejecutable, instalación y comandos de ayuda y versión.
El control completo del servicio IRC sigue en desarrollo. El siguiente hito es cerrar un
ciclo real de inicio, comprobación de disponibilidad, parada y limpieza.
