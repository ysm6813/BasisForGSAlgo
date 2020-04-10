---
layout: page
title: authors
permalink: /authors/
---

{% for author in site.authors %}
* [{{ author.name }}]({{ site.baseurl }}/authors/{{ author.name }})
{% endfor %}