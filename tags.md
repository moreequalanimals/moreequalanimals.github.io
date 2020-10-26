---
layout: post
title: All Topics
permalink: /tags/
content-type: eg
---

<style>
.category-content a {
    text-decoration: none;
    color: #4183c4;
}

.category-content a:hover {
    text-decoration: underline;
    color: #4183c4;
}
</style>

<main>
    {% for tag in site.tags %}
        <h3 id="{{ tag | first }}"><a href="/tags/{{tag|first}}">{{ tag | first | capitalize }}</a></h3>
    {% endfor %}
    <br/>
    <br/>
</main>
