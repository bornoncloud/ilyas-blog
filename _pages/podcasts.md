---
layout: page
title: podcasts
permalink: /podcast/
description: A growing collection of your cool podcasts.
nav: true
display_categories: [cloud stories]
horizontal: false
---

Bornonccloud podcast is a weekly podcast with technical tips and career advice for people working with cloud-native technologies. This show is for developers, IT pros, or anyone making a career move into the cloud. Episodes will be short and to the point and will regularly feature experts who share their experiences. This show is hosted by Ilyas F, a fifteen-year tech industry veteran, blooger, and Microsoft Azure MVP.  

<div class="projects">
  {% if site.enable_podcast_categories and page.display_categories %}
  <!-- Display categorized podcasts -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_podcasts = site.podcasts | where: "category", category %}
      {% assign sorted_podcasts = categorized_podcasts | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for podcast in sorted_podcasts %}
            {% include podcasts_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for podcast in sorted_podcasts %}
            {% include podcasts.html %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}

  {% else %}
  <!-- Display projects without categories -->
    {% assign sorted_podcasts = site.podcasts | sort: "importance" %}
    <!-- Generate cards for each podcast -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
        {% for podcast in sorted_podcasts %}
          {% include podcasts_horizontal.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for podcast in sorted_podcasts %}
          {% include podcasts.html %}
        {% endfor %}
      </div>
    {% endif %}

  {% endif %}

</div>
