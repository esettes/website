# Portfolio and Technical Blog

Roxana Stancu's portfolio, built with Jekyll and published through GitHub Pages.

The site contains:

- A professional profile and contact details.
- Six projects with detail pages.
- Two technical articles.

## Run locally

Ruby, Bundler, and the dependencies listed in `Gemfile` are required.

```bash
bundle install
bundle exec jekyll serve
```

The site will be available at:

```text
http://127.0.0.1:4000/website/
```

## Edit the profile

Contact details and profile copy live in `_data/profile.yml`. Technology icons are read
directly from `assets/images/icons/`; the `media/` subdirectory is reserved for the
GitHub, LinkedIn, and CV icons.

The About me page is served from the root path and edited in `index.md`.

## Add a project

Create a Markdown file in `_projects/` with front matter such as:

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

`priority` controls the list order. If `cover` is missing, the layout keeps an empty 3:2
placeholder.

## Add an article

Articles are stored in `_posts/` using Jekyll's filename format:

```text
YYYY-MM-DD-title.md
```

## Publishing

The repository currently uses the `master` branch. Configure GitHub Pages to publish from
that branch and the repository root.

Expected URL:

```text
https://esettes.github.io/website/
```
