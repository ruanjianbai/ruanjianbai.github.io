---
layout: post
title: "写博客"
date: 2015-06-12 18:26:10 +0800
comments: true
categories: 博客
---
写一篇博客的常用步骤，总结如下：

进入octopress目录并切换到source分支
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
预览博客
{% codeblock lang:bash  %}
rake generate
{% endcodeblock %}
在浏览器里打开 `http://localhost:4000/` 进行预览，

每次写完都要将本地 source 资源推送到 github 上
{% codeblock lang:bash  %}
git push origin source
{% endcodeblock %}

切换到master分支并合并source分支

{% codeblock lang:bash  %}
➜  octopress git:(source) ✗ git checkout master
➜  octopress git:(master) ✗ git merge source
{% endcodeblock %}

发布文章
{% codeblock lang:bash  %}
rake generate
rake deploy
{% endcodeblock %}

最好在发布前先预览一下，没有问题再deploy
{% codeblock lang:bash  %}
rake preview
{% endcodeblock %}
