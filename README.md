# Web personal para GitHub Pages

Base Jekyll preparada para una web profesional y academica con tres bloques:

- `home` para presentacion, contacto y CV.
- `blog` para ir anadiendo posts.
- `projects` como coleccion para proyectos con metadatos, imagenes y enlaces.

## Estructura

```text
.
├── _config.yml
├── _data/
│   ├── navigation.yml
│   └── profile.yml
├── _includes/
├── _layouts/
├── _posts/
├── _projects/
├── assets/
│   ├── css/
│   ├── files/cv/
│   └── images/
├── blog/
├── projects/
└── index.md
```

## Editar contenido

### Datos principales

Edita [`_data/profile.yml`](_data/profile.yml) para:

- nombre, tagline e introduccion
- enlaces de contacto
- resumen de CV
- destacados del home

Si subes tu CV en PDF, guardalo en `assets/files/cv/` y actualiza `resume.file`.

### Blog

Cada post va en [`_posts/`](_posts) con formato:

```md
---
title: "Titulo"
date: 2026-06-10 09:00:00 +0200
excerpt: "Resumen corto"
author: "Tu Nombre"
---
Contenido.
```

### Proyectos

Cada proyecto va en [`_projects/`](_projects) con formato:

```md
---
title: "Nombre proyecto"
date: 2026-06-10
excerpt: "Resumen corto"
status: "En curso"
role: "Tu rol"
stack:
  - Jekyll
  - GitHub Pages
repo_url: "https://github.com/tuusuario/tu-repo"
demo_url: ""
cover: "/assets/images/projects/portada.jpg"
gallery:
  - src: "/assets/images/projects/captura-1.jpg"
    alt: "Captura 1"
---
Descripcion completa.
```

## Desarrollo local

```bash
bundle install
bundle exec jekyll serve
```

## Publicacion en GitHub Pages

1. Sube repo a GitHub.
2. Activa GitHub Pages desde rama `main` y carpeta `/ (root)`.
3. Si publicas como proyecto y no como `usuario.github.io`, ajusta `baseurl` en [`_config.yml`](_config.yml).
