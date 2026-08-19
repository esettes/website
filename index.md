---
layout: default
title: About me
description: Perfil profesional de Roxana Stancu, desarrolladora de software en Madrid.
permalink: /
---
{% assign profile = site.data.profile %}
<article class="shell about-page">
  <header class="about-header">
    <p class="about-role">{{ profile.role }}</p>
    <h1>{{ profile.name }}</h1>
    <p class="about-intro">{{ profile.intro }}</p>
    <p>{{ profile.current }}</p>
    <p class="location">{{ profile.location }}</p>
  </header>

  <section class="about-section" aria-labelledby="contact-heading">
    <h2 id="contact-heading">Contacto</h2>
    <ul class="contact-list">
      <li>
        <strong>Email:</strong>
        <a href="mailto:{{ profile.email }}">{{ profile.email }}</a>
      </li>
      <li>
        <a href="{{ profile.github }}" target="_blank" rel="noopener noreferrer">
          <img class="professional-icon" src="{{ '/assets/images/icons/media/github.png' | relative_url }}" alt="">
          GitHub
        </a>
      </li>
      <li>
        <a href="{{ profile.linkedin }}" target="_blank" rel="noopener noreferrer">
          <img class="professional-icon" src="{{ '/assets/images/icons/media/linkedin.svg' | relative_url }}" alt="">
          LinkedIn
        </a>
      </li>
      <li>
        <a href="{{ profile.cv | relative_url }}" download>
          <img class="professional-icon" src="{{ '/assets/images/icons/media/cv.svg' | relative_url }}" alt="">
          Currículum
        </a>
      </li>
    </ul>
  </section>

  <section class="about-section" aria-labelledby="technologies-heading">
    <h2 id="technologies-heading">Tecnologías</h2>
    <ul class="technology-list">
      {% assign technology_icons = site.static_files | sort: 'path' %}
      {% for icon in technology_icons %}
        {% if icon.path contains '/assets/images/icons/' %}
          {% unless icon.path contains '/assets/images/icons/media/' %}
            <li>
              <img
                class="technology-icon"
                src="{{ icon.path | relative_url | replace: '#', '%23' }}"
                alt="{{ icon.basename | replace: '-', ' ' }}"
                title="{{ icon.basename | replace: '-', ' ' }}"
              >
            </li>
          {% endunless %}
        {% endif %}
      {% endfor %}
    </ul>
  </section>
</article>
