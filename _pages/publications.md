---
permalink: /publications/
title: "Publications"
author_profile: true
---


Here is my list of publications.  
They are auto-generated from my BibTeX file.  

For the most recent updates, please also visit my [Google Scholar profile](https://scholar.google.com/citations?user=iQbRc7kAAAAJ&hl=en&authuser=3){:target="_blank"}.


{% for pub in site.publications reversed %}
- {{ pub.citation }}
  {% if pub.paperurl %}
  [Access Paper]({{ pub.paperurl }}){:target="_blank"}
  {% endif %}
{% endfor %}
