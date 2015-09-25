---
layout: post
title: "写博客"
date: 2015-06-12 18:26:10 +0800
comments: true
categories: 博客
---
写一篇博客的常用步骤，总结如下：

首先新建博客

{% codeblock lang:java  %}
rake new_post["title"]
{% endcodeblock %}
这时候在source/_posts/目录下自动生成对应标题的markdown文件，在该文件里写文章

注：如果shell由bash切换到了zsh，则直接输入rake new_post,然后会提示输入标题，再输入标题就可以了

生成博客
{% codeblock lang:java  %}
rake generate
git add . 
git commit -m 'change log'
{% endcodeblock %}
预览博客
{% codeblock lang:java  %}
rake preview
{% endcodeblock %}
在浏览器里打开 http://localhost:4000/ 进行预览，

发布文章
{% codeblock lang:java  %}
rake deploy
{% endcodeblock %}

每次写完都要将本地source资源推送到github上
{% codeblock lang:java  %}
git push origin source
{% endcodeblock %}