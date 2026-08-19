---
title: "ft_irc"
priority: 1
date: 2026-08-10
excerpt: "Non-blocking IRC server in C++98 that handles multiple clients through a single poll loop."
status: "In development · 42 Madrid"
role: "Backend, IRC protocol, channels, and testing"
category: "Backend and networking"
code: "IRC"
stack:
  - C++98
  - TCP/IP
  - poll
  - IRC
  - Integration tests
repo_url: "https://github.com/esettes/42-ft_irc"
demo_url: ""
cover: "/assets/images/projects/ft_irc.png"
---
## The challenge

Build a server compatible with a real IRC client, without threads or additional processes,
using a single `poll()` call to accept connections, receive data, and send responses to
multiple clients simultaneously.

## Technical work

The server keeps state for each client, reconstructs complete lines from the TCP stream,
interprets commands, and generates responses in the IRC protocol format.

The work covers:

- Registration through `PASS`, `NICK`, and `USER`.
- Input and output buffers for partial operations.
- Numeric replies and IRC prefixes.
- A channel and client membership model.
- Channel commands such as `JOIN`, `TOPIC`, `INVITE`, `KICK`, and `MODE`.
- Tests with real clients, `netcat`, and automated cases.

## A key decision

TCP does not preserve message boundaries. A `recv()` call can return half a command or
several commands together. Each client therefore needs a persistent buffer, and the server
only processes a command after finding its `\r\n` terminator.

## Status

This is a team project and remains in development. The portfolio documentation will be
updated as the channel commands and their tests are completed.
