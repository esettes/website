# Portfolio & Technical Blog

Web profesional de Roxana Stancu, construida con Jekyll y publicada mediante GitHub Pages.

La página presenta:

- Perfil profesional y experiencia.
- Portfolio con casos de estudio detallados.
- Blog sobre backend, automatización, Linux, redes y testing.
- Información de contacto y disponibilidad profesional.

## Desarrollo local

Se necesita Ruby, Bundler y las dependencias incluidas en `Gemfile`.

```bash
bundle install
bundle exec jekyll serve
```

La web estará disponible en:

```text
http://127.0.0.1:4000/website/
```

## Editar el perfil

Los datos principales están en:

- `_data/profile.yml`: presentación, contacto, estado profesional y especialización.
- `_data/skills.yml`: tecnologías agrupadas por área.
- `about/index.html`: experiencia, formación y forma de trabajar.

## Añadir un proyecto

Crear un archivo Markdown dentro de `_projects/` con metadatos como:

```yaml
---
title: "Project title"
date: 2026-08-18
excerpt: "Short project description."
status: "In progress"
role: "Architecture and development"
category: "Backend"
code: "API"
stack:
  - Python
  - PostgreSQL
repo_url: "https://github.com/esettes/project"
demo_url: ""
cover: ""
---
```

Después del front matter se documentan el problema, la solución, las decisiones técnicas,
el resultado y el estado real del proyecto.

## Añadir un artículo

Los artículos se guardan en `_posts/` siguiendo el formato de Jekyll:

```text
YYYY-MM-DD-title.md
```

## Publicación

El repositorio usa actualmente la rama `master`. GitHub Pages debe configurarse para
publicar desde esa rama y el directorio raíz.

URL prevista:

```text
https://esettes.github.io/website/
```
