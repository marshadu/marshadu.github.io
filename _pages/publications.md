---
permalink: /publications/
title: "Publications"
author_profile: true
---

Here is my list of publications.  
They are auto-generated from my BibTeX file.

{% for pub in site.publications reversed %}
- {{ pub.citation }}
  {% if pub.paperurl %}
  [Access Paper]({{ pub.paperurl }}){:target="_blank"}
  {% endif %}
{% endfor %}
