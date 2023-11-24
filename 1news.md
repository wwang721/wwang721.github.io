---
layout: page
title: News
tagline:
permalink: /news.html
---

<div>

    <h2>Latest Posts</h2>

    <div>&nbsp;</div>

    <ul class="post-list">
        {% for post in site.posts %}
            <li style="height:220px; border: 0px solid black;">
                
                <div style="float: left; width: 250px; height: 210px; border: 0px solid red;">
                <div style="width:225px; height: 172px; border: 0px solid green; overflow:hidden; margin:10px auto auto 0px; display: flex; align-items: center;justify-content: center;">
                <a href="{{ post.url | relative_url }}" title="{{post.title}}">
                    {% assign date_format = "%Y-%m-%d" %}
                    <img src="images/posts/{{post.date|date:date_format}}.jpg" alt="Not available" title="{{post.title}}"
                    style="width:225px;">
                </a>
                </div>
                </div>

                
                {% assign date_format = site.cayman-blog.date_format | default: "%b %-d, %Y" %}
                <span class="post-meta">{{ post.date | date: date_format }}</span>

                <h2>
                    <a class="post-link" href="{{ post.url | relative_url }}" title="{{ post.title }}">{{ post.title |
                        escape }}</a>
                </h2>

                <span>{{ post.excerpt | markdownify | truncatewords: 30 }}

        {% endfor %}