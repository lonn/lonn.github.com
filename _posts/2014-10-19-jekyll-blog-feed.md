---
layout: post
title: 为 Jekyll 博客添加 RSS feed
date: 2014-10-19 12:00:00
---
{% raw %}
为博客添加 RSS feed，不仅能方便别人订阅，自己也能利用它制作 IFTTT action，同步推送到各种 social network。

由于本人博客是基于 Jekyll，而且是相当的简单，参考 [jekyll-rss-feeds](https://github.com/snaptortoise/jekyll-rss-feeds)，做法如下：

###1. 给你的 Jekyll 网站添加 site details
在 `_config.yml` file 添加下列属性：

```
name:         Your Blog's Name
description:  A description for your blog
url:          http://your-blog-url.com
```

这些值 `{{ site.name }}`，`{{ site.description }}`，`{{ site.url }}` 会在你的 feed 文件里用到。

###2. 在网站根目录下添加 feed.xml
在 [jekyll-rss-feeds](https://github.com/snaptortoise/jekyll-rss-feeds) 这个项目里面，会有几个 feeds template，选择你想要的，我选择的是 `feed.xml`，代码如下：

``` html
---
layout: none
---
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:atom="http://www.w3.org/2005/Atom">
    <channel>
        <title>{{ site.name | xml_escape }}</title>
        <description>{% if site.description %}{{ site.description | xml_escape }}{% endif %}</description>      
        <link>{{ site.url }}</link>
        <atom:link href="{{ site.url }}/feed.xml" rel="self" type="application/rss+xml" />
        {% for post in site.posts limit:10 %}
            <item>
                <title>{{ post.title | xml_escape }}</title>
                <description>{{ post.content | xml_escape }}</description>
                <pubDate>{{ post.date | date: "%a, %d %b %Y %H:%M:%S %z" }}</pubDate>
                <link>{{ site.url }}{{ post.url }}</link>
                <guid isPermaLink="true">{{ site.url }}{{ post.url }}</guid>
            </item>
        {% endfor %}
    </channel>
</rss>
```

修改 `{% for post in site.posts limit:10 %}` 中的数字 `10` ，将规定你的 feed 里的最近文章数。

###3. Build and push

That's it. `jekyll build` 你的网站然后 push，大功告成。本站的 feed：[http://liuyuel.com/feed.xml](http://liuyuel.com/feed.xml)

{% endraw %}