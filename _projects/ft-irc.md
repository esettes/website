---
title: "ft_irc: servidor IRC no bloqueante"
date: 2026-08-10
excerpt: "Servidor IRC en C++98 capaz de gestiónar múltiples clientes mediante sockets no bloqueantes y un único bucle poll."
status: "En desarrollo · 42 Madrid"
role: "Backend, protocolo IRC, canales y testing"
category: "Backend y networking"
code: "IRC"
stack:
  - C++98
  - TCP/IP
  - poll
  - IRC
  - Integration tests
repo_url: "https://github.com/esettes/42-ft_irc"
demo_url: ""
cover: ""
---
## El reto

Construir un servidor compatible con un cliente IRC real, sin threads ni procesos
adicionales y usando un único `poll()` para aceptar conexiónes, recibir datos y enviar
respuestas a varios clientes simultaneamente.

## Trabajo técnico

El servidor mantiene estado por cliente, reconstruye líneas completas a partir del flujo
TCP, interpreta comandos y genera respuestas con el formato del protocolo IRC.

Entre las áreas trabajadas se encuentran:

- Registro mediante `PASS`, `NICK` y `USER`.
- Buffers de entrada y salida para operaciónes parciales.
- Mensajes numericos y prefijos IRC.
- Modelo de canales y pertenencia de clientes.
- Comandos de canal como `JOIN`, `TOPIC`, `INVITE`, `KICK` y `MODE`.
- Pruebas con clientes reales, `netcat` y casos automatizados.

## Una decisión importante

TCP no conserva los límites entre mensajes. Una llamada a `recv()` puede devolver medio
comando o varios comandos juntos. Por ello cada cliente necesita un buffer persistente
y el servidor solo procesa una orden cuando encuentra su terminador `\r\n`.

## Estado

El proyecto se desarrolla en equipo y continúa en implementación. La documentación del
portfolio se actualizará a medida que los comandos de canal y sus pruebas queden cerrados.
