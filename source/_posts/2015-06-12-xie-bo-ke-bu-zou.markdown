---
layout: post
title: "写博客"
date: 2015-06-12 18:26:10 +0800
comments: true
categories: 博客
---
写一篇博客的常用步骤，总结如下：

进入 octopress 目录切换到 source 分支（默认）
{% codeblock lang:bash  %}
➜  ~ cd octopress
➜  octopress git:(source) ✗ git checkout source
{% endcodeblock %}

首先新建博客

{% codeblock lang:bash  %}
rake new_post["title"]
{% endcodeblock %}
这时候在`source/_posts/`目录下自动生成对应标题的 markdown 文件，在该文件里写文章

注：如果 shell 由 bash 切换到了 zsh ，则直接输入`rake new_post`，然后会提示输入标题，再输入标题就可以了
<!--more-->
生成博客
{% codeblock lang:bash  %}
rake generate
git add . 
git commit -m 'change log'
{% endcodeblock %}
说明：执行了`rake generate`后实际上是将生成好的要发布的内容放到`_deploy`目录

预览博客
{% codeblock lang:bash  %}
rake preview
{% endcodeblock %}
在浏览器里打开 `http://localhost:4000/` 进行预览，

发布文章
{% codeblock lang:bash  %}
rake deploy
{% endcodeblock %}
说明：执行了`rake deploy`后实际上是直接将`_deploy`文件夹的内容推送到远程`master`分支

每次写完都要将本地 source 资源推送到 github 上
{% codeblock lang:bash  %}
git push origin source
{% endcodeblock %}

总的来说，在 source 分支写博客，生成内容，将`_deploy`推送到`master`分支显示博客内容，将博客源码推送到远程 source 分支。