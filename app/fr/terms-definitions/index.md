---
layout: page
title: "Termes et définitions"
lead: "Toutes les définitions des termes utilisés dans cette documentation."
locale: "fr"
updated: "2008-12-14 10:30:00 +0900"
---

<dl>
{% assign sorted_defs = site.data.fr.definitions | sort: 'word' %}
{% for def in sorted_defs %}
  <dt id="{{ def.anchor }}">{{ def.word }}</dt>
  <dd>{{ def.definition }}</dd>
{% endfor %}
</dl>