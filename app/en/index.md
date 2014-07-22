---
layout: page
title: "Check my Website documentation"
locale: "en"
lead: "Welcome to the english version of the Check my Website service documentation."
---

## What can you find here ?

The documentation is divided in four parts : 

1. [FAQ](/en/faq/)
2. [Howtos](/en/howtos)
3. [Console](/en/console)
4. [API](/en/api/)

## Terminology and definitions

<dl>
{% assign sorted_defs = site.data.en.definitions | sort: 'word' %}
{% for def in sorted_defs %}
  <dt id="{{ def.word | replace:' ','-' | downcase }}">{{ def.word }}</dt>
  <dd>{{ def.definition }}</dd>
{% endfor %}
</dl>

## Convention

Console, technical words, menus and keyboard shortcuts are `highlighted`.

When buttons are dimmed in the console, it indicates that the function is not available.

## Contribute

We try to keep this documentation as accurate as possible but if you find mistakes or parts that seems to be outdated, you can open a ticket on our helpdesk system. You can also fork, modify an dmake a pull request. Thansk in advance for any cooperation.
