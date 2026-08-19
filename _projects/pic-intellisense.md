---
title: "PIC IntelliSense"
priority: 4
date: 2026-08-12
excerpt: "Extensión en TypeScript con autocompletado, hover e importación automática de metadatos para desarrollo C orientado a PIC."
status: "En desarrollo"
role: "Diseño de producto, extensión, tooling y pruebas"
category: "Developer tooling"
code: "PIC++"
stack:
  - TypeScript
  - VS Code API
  - C
  - Tooling
  - Testing
repo_url: "https://github.com/esettes/PIC_Intellisense"
demo_url: ""
cover: "/assets/images/projects/PIC IntelliSense.png"
---
## El problema

El desarrollo para PIC utiliza registros y cabeceras específicos de cada dispositivo.
Mantener manualmente completions y documentación para cada modelo no es escalable.

## La solución

Una extensión de Visual Studio Code que aporta:

- Autocompletado de registros y helpers habituales.
- Documentación contextual mediante hover.
- Snippets para flujos comunes de inicialización.
- Filtrado según el dispositivo seleccionado.
- Herramientas para importar metadatos desde headers XC8 o Device Family Packs locales.

## Arquitectura

La extensión separa providers, modelos, datos manuales, datos generados y tooling de
importación. Los datos curados tienen prioridad sobre los generados, lo que permite
automatizar la cobertura sin perder explicaciones escritas a mano.

El comando de configuración detecta instalaciones de XC8, valida sus rutas y crea o
combina una configuración `c_cpp_properties.json` sin destruir configuraciones previas.

## Calidad y límites

El proyecto incluye compilación, lint, tests y empaquetado VSIX. El importador usa un
parser basado en expresiones regulares y documenta los dialectos de cabeceras que aún
no cubre. Esa limitación se trata como una frontera de producto, no como un detalle oculto.
