---
layout: page
title: Siege
description: "Various guides and tools about Rainbow Six: Siege, migrated from siege.dangeraspect.xyz"
parent: none
---

<ul class="link-collection">
{% for item in site.siege %}
    <li class="link">
        <a href="{{ item.url }}">
        <div class="link-title">{{ item.title }}</div>
            <div class="link-description">
                {{ item.description }}
                <br>
                Last updated: {{ item.date | date_to_string}}
            </div>
        </a>
    </li>
{% endfor %}
</ul>