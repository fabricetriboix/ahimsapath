---
layout: page
title: Tags
permalink: /tags/
---

<script>
function toggle(divname) {
    var el = document.getElementById(divname);
    if (el.style.display == "none") {
        el.style.display = "block";
    } else {
        el.style.display = "none";
    }
}
</script>

{% for tag in site.tags %}
  {% capture tag_name %}{{ tag | first }}{% endcapture %}
  {% assign tag_id = tag_name | slugify %}
  <h1><a onclick="toggle('{{ tag_id }}')">{{ tag_name }}</a></h1>
  <div id="{{ tag_id }}" style="display:none">
    <ul>
      {% for post in site.tags[tag_name] %}
        <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>
  </div>
{% endfor %}
