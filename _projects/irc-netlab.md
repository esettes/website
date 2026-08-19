---
title: "QA network lab"
priority: 3
date: 2026-08-03
excerpt: "Reproducible Python lab for starting, observing, testing, and cleaning up IRC services automatically."
status: "Initial phase · In development"
role: "Requirements, architecture, implementation, and QA"
category: "Automation and testing"
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
## Goal

Reliably testing a network server requires more than sending commands. The test environment
must control its lifecycle, detect when it is ready, preserve evidence, and clean up every
resource even when a test fails.

`irc-netlab` is a standalone lab designed to run that cycle reproducibly:

```text
validate -> start -> wait until ready -> test -> stop -> clean up
```

## Architecture principles

- The lab can run without an external orchestrator.
- It exposes capabilities through public, documented contracts.
- It does not depend on future HTTP, TCP, DNS, or WebSocket labs.
- Each phase must return structured results and useful diagnostic evidence.
- Cleanup is part of the result, not a secondary task.

## Technical foundation

The project uses Python 3.12, a `src` layout, an installable CLI, unit and integration
tests, Ruff, wheel builds, and documented architecture decisions.

## Current status

The first phase provides the executable foundation, installation, and help and version
commands. Full IRC service control remains in development. The next milestone is a complete
cycle covering startup, readiness checks, shutdown, and cleanup.
