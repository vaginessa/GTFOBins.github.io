---
layout: page
title: Functions
---

A binary may support one or more of the following functions:

<dl class="function-list">
    {% for function_pair in site.data.functions %}
    {% assign function = function_pair[1] %}
    <dt>{{ function.label }}</dt>
    <dd>{{ function.description | markdownify }}</dd>
    {% endfor %}
</dl>
