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
            <li style="height:220px; border: 1px solid red;">
                
                <div style="float: left; width: 250px; height: 210px; border: 1px solid white;">
                <div style="width: 250px; height: 172px; border: 1px solid white; overflow:hidden;">
                <a href="{{ post.url | relative_url }}" target="_blank" title="{{post.title}}">
                    {% assign date_format = "%Y-%m-%d" %}
                    <img src="images/posts/{{post.date|date:date_format}}.jpg" alt="Not available" title="{{post.title}}"
                    style="width:225px; margin:8px 0px 0px 0px">
                </a>
                </div>
                </div>

                
                {% assign date_format = site.cayman-blog.date_format | default: "%b %-d, %Y" %}
                <span class="post-meta">{{ post.date | date: date_format }}</span>

                <h2>
                    <a class="post-link" href="{{ post.url | relative_url }}" title="{{ post.title }}" target="_blank">{{ post.title |
                        escape }}</a>
                </h2>

                <span>{{ post.excerpt | markdownify | truncatewords: 30 }}</span>
            </li>
        {% endfor %}
    </ul>
</div>


<p style="float:none; margin:0px 0px 0px 0px; height:200px; border: 11px solid black;">&ensp;</p>
<div>&nbsp;</div>

<a href="{{ site.url }}{{ site.baseurl }}"><b><u>Back to the Home page</u></b></a>