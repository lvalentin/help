---
layout: page
title: "Termes et définitions"
lead: "Toutes les termes et définitions utilisés dans cette documentation."
locale: "fr"
updated: "2008-12-14 10:30:00 +0900"
---

<dl>
{% assign sorted_defs = site.data.fr.definitions | sort: 'word' %}
{% for def in sorted_defs %}
  <dt id="{{ def.word | replace:' ','-' | downcase }}">{{ def.word }}</dt>
  <dd>{{ def.definition }}</dd>
{% endfor %}
</dl>