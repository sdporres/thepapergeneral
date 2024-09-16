---
layout: page
title: Wiki
---

```text
This section of the site describes the various parts and mechanics of the game in the hope that it will enable YOU to go about ruling your realm.
```

{% assign section-entries = site.domesday-entries | where: "section", "Basics" %}
{% if section-entries.size > 0 %}
  <h2> {{ section-entries.first.section }} </h2>
  <ul class="horz">
  {% for entry in section-entries %}
    <li><a href="{{ entry.url }}">{{ entry.title }}</a></li>
    {% unless entry == section-entries.last %} - {% endunless %}  
  {% endfor %}
  </ul>
{% endif %}

{% assign section-entries = site.domesday-entries | where: "section", "Personal Commands" %}
{% if section-entries.size > 0 %}
  <h2> {{ section-entries.first.section }} </h2>
  <ul class="horz">
  {% for entry in section-entries %}
    <li><a href="{{ entry.url }}">{{ entry.title }}</a></li>
    {% unless entry == section-entries.last %} - {% endunless %}  
  {% endfor %}
  </ul>
{% endif %}

{% assign section-entries = site.domesday-entries | where: "section", "Captain Commands" %}
{% if section-entries.size > 0 %}
  <h2> {{ section-entries.first.section }} </h2>
  <ul class="horz">
  {% for entry in section-entries %}
    <li><a href="{{ entry.url }}">{{ entry.title }}</a></li>
    {% unless entry == section-entries.last %} - {% endunless %}  
  {% endfor %}
  </ul>
{% endif %}

{% assign section-entries = site.domesday-entries | where: "section", "Advanced" %}
{% if section-entries.size > 0 %}
  <h2> {{ section-entries.first.section }} </h2>
  <ul class="horz">
  {% for entry in section-entries %}
    <li><a href="{{ entry.url }}">{{ entry.title }}</a></li>
    {% unless entry == section-entries.last %} - {% endunless %}  
  {% endfor %}
  </ul>
{% endif %}

---

## The Domesday Book

<div class="smaller-text">
In 1066 William I conquered England, earning his famous nickname and ending years of Saxon and Scandavian dominance over the island. Almost 20 years later, in 1085, William sent out his stewards and scribes to travel the whole breadth of the realm and record everything they found.</div>

![domesday-book](/public/images/domesday/250px-Domesday-book-1804x972.jpg){: .center }

<span class="smaller-text">The historical Domesday Book</span><sup class="smallest-text">[1](#footer)</sup> <span class="smaller-text"> was a survey of all the lands, titles and estates throughout the British isles. The book was massive and took around two years to complete. It contained all the information William needed to govern the realm.</span>

---

<span class="smaller-text"><a name="footer"><sup>1 </sup></a>Read about the real Domesday Book: [https://en.wikipedia.org/wiki/Domesday_Book](https://en.wikipedia.org/wiki/Domesday_Book)</span>


