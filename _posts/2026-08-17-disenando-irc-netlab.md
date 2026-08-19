---
title: "Designing irc-netlab: a reproducible lab for testing IRC"
date: 2026-08-17 18:00:00 +0200
excerpt: "How to separate the lab, the service under test, and a future orchestrator to obtain repeatable results."
description: "Architecture principles and the initial scope of irc-netlab."
author: "Roxana Stancu"
cover: "/assets/images/blog/netlab.png"
---
A protocol test can send commands and check responses. A QA lab must also control
everything that happens before and after that exchange.

`irc-netlab` is my project for building that environment around an IRC service.

<!--more-->

## The complete cycle

The first goal is not to support every imaginable scenario. It is to achieve a small,
reliable, and repeatable local cycle:

```text
validate
-> start
-> wait until ready
-> report status
-> stop
-> clean up
-> report result
```

Every step needs an observable result. If the service does not start, the lab must explain
why. If a test fails, it must preserve evidence. If execution ends unexpectedly, it must
still clean up the processes and resources it owns.

## Independence before generalization

`irc-netlab` will be the first lab in an ecosystem that could include HTTP, TCP, DNS, or
WebSocket. That does not mean they should all share a large abstraction from day one.

The initial rules are:

- Each lab exposes capabilities through public contracts.
- Labs do not depend on one another.
- A lab must work without the orchestrator.
- The future `netlab-qa` consumes contracts; it does not become a dependency of the labs.

This direction makes it possible to learn from a real implementation before designing a
generic platform that might not match actual needs.

## An installable and verifiable foundation

The first phase focuses on the foundation:

- Python 3.12 and a `src` layout.
- An installable package and console entry point.
- A CLI with help, version, and defined exit codes.
- Unit and integration tests.
- Ruff and validation of the generated wheel.
- Documented requirements, architecture, and decisions.

This foundation does not yet run the complete cycle. Publishing that limitation avoids
confusing a sound project structure with functionality that does not yet exist.

## Next milestone

The next useful result will be controlling a real IRC service from start to finish: starting
it, detecting readiness, stopping it, and proving that no orphaned resources remain. From
there, each additional capability can grow from real evidence.
