# Portfolio and Technical Blog

Portfolio de Roxana Stancu, construido con Jekyll y publicado mediante GitHub Pages.

El sitio contiene:

- Perfil profesional y datos de contacto.
- Seis proyectos con páginas de detalle.
- Dos artículos técnicos.

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

Los datos de contacto y el texto principal están en `_data/profile.yml`. Los iconos de
tecnologías se leen directamente de `assets/images/icons/`; la subcarpeta `media/` queda
reservada para los iconos de GitHub, LinkedIn y currículum.

La página About me se encuentra en la ruta raíz y se edita en `index.md`.

## Añadir un proyecto

Crear un archivo Markdown dentro de `_projects/` con metadatos como:

```yaml
---
title: "Project title"
priority: 7
excerpt: "Short project description."
status: "In progress"
role: "Architecture and development"
category: "Backend"
stack:
  - Python
  - PostgreSQL
repo_url: "https://github.com/esettes/project"
cover: "/assets/images/projects/project.png"
---
```

`priority` controla el orden del listado. Si falta `cover`, el diseño conserva un hueco
vacío con relación 3:2.

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
