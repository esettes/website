---
title: "pic16cc"
priority: 3
date: 2026-08-15
excerpt: "Compilador experimental escrito en Rust que transforma un subconjunto de C en firmware Intel HEX e incluye un simulador de CPU."
status: "Experimental · En desarrollo"
role: "Arquitectura, desarrollo, testing y documentación"
category: "Compiladores y sistemas embebidos"
code: "C→HEX"
stack:
  - Rust
  - C
  - PIC16
  - Intel HEX
  - Testing
repo_url: "https://github.com/esettes/PIC16_compiler"
demo_url: ""
cover: "/assets/images/projects/pic16cc.png"
---
## El problema

Los microcontroladores PIC16 trabajan con recursos muy limitados y suelen depender de
toolchains específicas. Este proyecto explora cómo construir una cadena de compilación
comprensible de principio a fin, desde código C hasta un archivo listo para programar.

## La solución

`pic16cc` compila un subconjunto de C directamente a Intel HEX sin necesitar un
ensamblador externo. El repositorio incluye dos herramientas:

- `picc`, responsable de analizar, optimizar y generar el firmware.
- `pic16-sim`, un simulador para ejecutar y comprobar el resultado sin hardware.

El flujo completo queda así:

```text
Código C -> frontend -> optimización -> código máquina -> firmware.hex
                                                     -> simulador PIC16
```

## Decisiones técnicas

- Arquitectura por etapas para poder probar cada fase de forma independiente.
- Generación adicional de mapas de símbolos y listados de instrucciones.
- Perfiles configurables para equilibrar tamaño de código y funcionalidad.
- Validación final del archivo HEX antes de considerarlo una salida correcta.
- Documentación explícita de las limitaciones del subconjunto de C soportado.

## Resultado actual

El compilador soporta dos dispositivos PIC16, tipos enteros, estructuras, arrays,
interrupciones y un conjunto limitado de operaciones en coma flotante. Sigue siendo
experimental y no pretende sustituir una toolchain de producción.

Este proyecto demuestra diseño de compiladores, arquitectura de sistemas, testing y
capacidad para trabajar cerca del hardware sin esconder las limitaciones reales.
