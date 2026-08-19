---
title: "Diseñando irc-netlab: un laboratorio reproducible para probar IRC"
date: 2026-08-17 18:00:00 +0200
excerpt: "Cómo separar el laboratorio, el servicio probado y el futuro orquestador para obtener resultados repetibles."
description: "Principios de arquitectura y alcance inicial de irc-netlab."
author: "Roxana Stancu"
---
Una prueba de protocolo puede enviar comandos y comprobar respuestas. Un laboratorio de
QA necesita controlar también todo lo que ocurre antes y después de esa conversación.

`irc-netlab` es mi proyecto para construir ese entorno alrededor de un servicio IRC.

<!--more-->

## El ciclo completo

El primer objetivo no es soportar todos los escenarios imaginables. Es conseguir un ciclo
local pequeño, fiable y repetible:

```text
validate
-> start
-> wait until ready
-> report status
-> stop
-> clean up
-> report result
```

Cada paso necesita un resultado observable. Si el servicio no arranca, el laboratorio debe
explicar por qué. Si una prueba falla, debe conservar evidencia. Si la ejecución termina de
forma inesperada, aún debe limpiar los procesos y recursos que le pertenecen.

## Independencia antes que generalización

`irc-netlab` será el primer laboratorio de un ecosistema que podría incluir HTTP, TCP, DNS
o WebSocket. Eso no significa que todos deban compartir una gran abstracción desde el día uno.

Las reglas iniciales son:

- Cada laboratorio expone capacidades mediante contratos públicos.
- Los laboratorios no dependen entre sí.
- Un laboratorio debe poder utilizarse sin el orquestador.
- El futuro `netlab-qa` consume contratos; no se convierte en dependencia de los laboratorios.

Esta dirección permite aprender de una implementación real antes de diseñar una plataforma
genérica que podría no corresponderse con las necesidades reales.

## Una base instalable y verificable

La primera fase se centra en los cimientos:

- Python 3.12 y estructura `src`.
- Paquete instalable y ejecutable de consola.
- CLI con ayuda, versión y códigos de salida definidos.
- Tests unitarios y de integración.
- Ruff y validación de la wheel generada.
- Requisitos, arquitectura y decisiones documentadas.

Esta base no ejecuta aún el ciclo completo. Publicar ese límite evita confundir una buena
estructura de proyecto con una funcionalidad que todavía no existe.

## Siguiente hito

El siguiente resultado valioso será controlar un servicio IRC real de principio a fin:
iniciarlo, detectar que está disponible, detenerlo y demostrar que no quedan recursos
huérfanos. A partir de ahí, cada capacidad adicional podrá crecer sobre evidencia real.
