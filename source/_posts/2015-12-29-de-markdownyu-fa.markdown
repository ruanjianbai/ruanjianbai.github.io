---
layout: post
title: "常用的markdown语法"
date: 2015-12-29 15:35:11 +0800
comments: true
categories: 博客
---
原始markdown命令不被octopress解析
{% codeblock lang:java  %}
{% raw %}
{% codeblock [lang:language] [title] [url] [link text] %}
code snippet
{% endcodeblock %}
{% endraw %}
{% endcodeblock %}

{% raw %}{{ page.title }}{% endraw %} {% raw %}{{ page.url }}{% endraw %}