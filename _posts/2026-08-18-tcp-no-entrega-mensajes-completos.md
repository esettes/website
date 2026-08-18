---
title: "TCP no entrega mensajes completos: framing en un servidor IRC"
date: 2026-08-18 19:00:00 +0200
excerpt: "Por qué recv() puede devolver medio comando o varios a la vez, y cómo reconstruir líneas IRC sin perder datos."
description: "Una explicación práctica del buffering y el framing de mensajes IRC sobre TCP."
author: "Roxana Stancu"
---
Cuando probamos un servidor IRC con `netcat`, es fácil asumir que cada vez que pulsamos
Enter el servidor recibira exactamente un comando. TCP no ofrece esa garantia.

TCP transporta un **flujo ordenado de bytes**. Conserva el orden y permite detectar el
cierre de la conexión, pero no conoce los límites lógicos de los mensajes IRC.

<!--more-->

## Tres resultados válidos de recv()

Si el cliente envia:

```text
NICK rox\r\n
USER roxana 0 * :Roxana Stancu\r\n
```

el servidor podría recibir:

1. Los dos comandos en una sola llamada.
2. Un comando por llamada.
3. Fragmentos como `NI`, `CK rox\r\nUSER ro` y el resto más tarde.

Los tres casos son correctos desde el punto de vista de TCP. Por eso no debemos ejecutar
directamente todo lo que devuelve `recv()` como si fuese un mensaje completo.

## Un buffer persistente por cliente

Cada conexión necesita conservar los bytes que todavía no forman una línea completa. El
algoritmo conceptual es:

```text
append received bytes to the client buffer
while the buffer contains CRLF
    extract one complete line
    remove that line from the buffer
    parse and dispatch the command
keep the remaining partial data for the next read event
```

El detalle importante es el ultimo paso. El fragmento restante no es un error ni debe
descartarse: puede ser el principio del siguiente comando.

## Varias líneas en la misma lectura

Procesar solo la primera línea tampoco basta. Cuando llegan varios comandos juntos, el
servidor debe seguir extrayendo líneas hasta que el buffer ya no contenga un terminador
completo. El orden de procesamiento tiene que ser el mismo que el orden recibido.

Esto explica un fallo frecuente: las pruebas manuales funcionan comando a comando, pero
fallan al pegar un bloque completo de registro. El problema no está necesariamente en
`PASS`, `NICK` o `USER`; puede estar en la capa que separa el flujo TCP en líneas IRC.

## Limites y seguridad

Un buffer sin límites permitiría que un cliente enviase datos indefinidamente sin cerrar
una línea. Una implementación robusta debe definir:

- Longitud máxima aceptada para una línea IRC.
- Tamaño máximo del buffer pendiente.
- Comportamiento ante datos inválidos o una conexión cerrada a mitad de mensaje.
- Pruebas para fragmentacion, concatenacion y escrituras parciales.

## La idea que conviene recordar

Los protocolos orientados a líneas viven encima de TCP, pero sus mensajes no coinciden
con las lecturas del socket. El framing es responsabilidad de la aplicación.
