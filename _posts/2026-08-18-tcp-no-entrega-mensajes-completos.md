---
title: "TCP does not deliver complete messages: framing in an IRC server"
date: 2026-08-18 19:00:00 +0200
excerpt: "Why recv() can return half a command or several commands at once, and how to reconstruct IRC lines without losing data."
description: "A practical explanation of buffering and IRC message framing over TCP."
author: "Roxana Stancu"
cover: "/assets/images/blog/tcp.png"
---
When testing an IRC server with `netcat`, it is easy to assume that every press of Enter
will deliver exactly one command to the server. TCP provides no such guarantee.

TCP transports an **ordered stream of bytes**. It preserves order and lets us detect when
the connection closes, but it does not know the logical boundaries of IRC messages.

<!--more-->

## Three valid recv() results

If the client sends:

```text
NICK rox\r\n
USER roxana 0 * :Roxana Stancu\r\n
```

the server could receive:

1. Both commands in one call.
2. One command per call.
3. Fragments such as `NI`, `CK rox\r\nUSER ro`, and the remainder later.

All three cases are valid from TCP's perspective. We therefore must not process everything
returned by `recv()` as though it were a complete message.

## A persistent buffer for each client

Each connection must preserve the bytes that do not yet form a complete line. The
conceptual algorithm is:

```text
append received bytes to the client buffer
while the buffer contains CRLF
    extract one complete line
    remove that line from the buffer
    parse and dispatch the command
keep the remaining partial data for the next read event
```

The last step is important. The remaining fragment is not an error and must not be
discarded: it may be the beginning of the next command.

## Multiple lines in one read

Processing only the first line is also insufficient. When several commands arrive together,
the server must keep extracting lines until the buffer no longer contains a complete
terminator. Processing order must match receive order.

This explains a common bug: manual tests work command by command but fail when a complete
registration block is pasted. The problem is not necessarily in `PASS`, `NICK`, or `USER`;
it may be in the layer that separates the TCP stream into IRC lines.

## Limits and safety

An unbounded buffer would allow a client to send data indefinitely without completing a
line. A robust implementation must define:

- The maximum accepted IRC line length.
- The maximum pending buffer size.
- Behavior for invalid data or a connection closed midway through a message.
- Tests for fragmentation, concatenation, and partial writes.

## The key idea

Line-oriented protocols run on top of TCP, but their messages do not align with socket
reads. Framing is the application's responsibility.
