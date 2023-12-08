---
layout: page
title: News
tagline:
permalink: /news.html
---

<div>

    <h2>Latest Posts</h2>

    <div>&nbsp;</div>

    <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    <div id="fb-root"></div>
    <script async defer crossorigin="anonymous" src="https://connect.facebook.net/en_US/sdk.js#xfbml=1&version=v18.0"
    nonce="bvIXSjwe"></script>
    <ul class="post-list">
        {% for post in site.posts %}
            {% assign date_format = "%Y-%m-%d" %}
            <li id="{{post.date|date:date_format}}_row" style="border: 0px solid black; overflow: hidden">

                
                <div id="{{post.date|date:date_format}}_left" style="float: left; width: 325px; height: 185px; border: 0px solid red;">
                <div style="width:280px; height: 172px; border: 1px solid #E5E4E2; overflow:hidden; display: flex; align-items: center; justify-content: center; box-shadow: 0 0px 8px 0 rgba(0, 0, 0, 0.2), 0 0px 8px 0px rgba(0, 0, 0, 0.19);">
                <a href="{{ post.url | relative_url }}" title="{{post.title}}">
                    <img src="{{ post.image }}" alt="Not available" title="{{post.title}}"
                    style="width:280px;">
                </a>
                </div>
                </div>

                
                
                <div id="{{post.date|date:date_format}}_right" style="float: left; min-width:355px; border: 0px solid green;">

                {% assign date_format = site.cayman-blog.date_format | default: "%b %-d, %Y" %}
                <span class="post-meta">{{ post.date | date: date_format }} 
                </span>

                <h2 style="margin:auto auto 8px auto">
                    <a class="post-link" href="{{ post.url | relative_url }}" title="{{ post.title }}">{{ post.title |
                        escape }}</a>
                </h2>

                <span>{{ post.excerpt | markdownify | truncatewords: 30 }}

                <div class="row" style="margin:-5px 0 0 0px; overflow:hidden">
                <div class="column" style="float:left; width:75px;">
                <p style="">
                <a href="https://twitter.com/intent/tweet" class="twitter-share-button" data-show-count="false" data-text="{{post.title}} via @{{site.twitter_username}}" data-url="{{ post.url | absolute_url}}" data-size="small">Tweet</a>
                </p>
                </div>

                <div class="column" style="float:left; width:75px">
                <div class="fb-share-button" data-href="{{post.url | absolute_url}}" data-layout="button" data-size="small" style="display: flex;">
                </div>
                </div>

                </div>

                <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.3/jquery.min.js"></script>
                {% assign date_format = "%Y-%m-%d" %}
                <script>
                    // var scripts = document.getElementsByTagName("script");
                    // var thisScript = scripts[scripts.length - 1];
                    // var name = thisScript.id
                    var name = "{{post.date|date:date_format}}";
                    var r_w = $("#"+name+"_row").width();
                    var lc_w = $("#"+name+"_left").width();
                    $("#"+name+"_right").width(0.98*(r_w-lc_w));
                </script>
        {% endfor %}



