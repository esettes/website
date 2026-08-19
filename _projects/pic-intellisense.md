---
title: "PIC IntelliSense"
priority: 5
date: 2026-08-12
excerpt: "TypeScript extension with completion, hover documentation, and automatic metadata imports for PIC-oriented C development."
status: "In development"
role: "Product design, extension development, tooling, and testing"
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
## The problem

PIC development uses registers and headers specific to each device. Manually maintaining
completions and documentation for every model does not scale.

## The solution

A Visual Studio Code extension that provides:

- Completion for registers and common helpers.
- Contextual hover documentation.
- Snippets for common initialization flows.
- Filtering based on the selected device.
- Tools for importing metadata from local XC8 headers or Device Family Packs.

## Architecture

The extension separates providers, models, manually curated data, generated data, and
import tooling. Curated data takes precedence over generated data, allowing broader
coverage without losing hand-written explanations.

The configuration command detects XC8 installations, validates their paths, and creates
or merges a `c_cpp_properties.json` configuration without destroying existing settings.

## Quality and limitations

The project includes compilation, linting, tests, and VSIX packaging. The importer uses a
regular-expression parser and documents the header dialects it does not yet support. This
limitation is treated as a product boundary rather than a hidden implementation detail.
