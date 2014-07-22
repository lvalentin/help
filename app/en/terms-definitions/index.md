---
layout: page
title: "Terms and definitions"
lead: "All terms and definitions used in this documentation."
locale: "en"
updated: "2008-12-14 10:30:00 +0900"
---

<dl>
{% assign sorted_defs = site.data.en.definitions | sort: 'word' %}
{% for def in sorted_defs %}
  <dt id="{{ def.word | replace:' ','-' | downcase }}">{{ def.word }}</dt>
  <dd>{{ def.definition }}</dd>
{% endfor %}
</dl>