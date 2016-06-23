---
layout: post
title: "常用的 Markdown 语法"
date: 2015-12-29 15:35:11 +0800
comments: true
categories: 博客
---
所有用到过的 Markdown 语法都总结记录在这里，持续更新。

代码块语法高亮语法：
	{% raw %}
	{% codeblock [lang:language] [title] [url] [link text] %}
	code snippet
	{% endcodeblock %}
	{% endraw %}
	
或者

	``` [language] [title] [url] [link text]
	code snippet
	```
单纯的代码块不显示行号以及语法高亮，只需要另起一行按`tab键`
<!--more-->
标题语法：
	
	{% raw %}
	#
	{% endraw %}


几级标题就用几个井号

命令、路径等内容通常使用如下语法，标示突出

	`这个地方就是是命令或路径等关键字`

遇到原始语法关键字不被 Octopress 解析的情况，需要使用 &#123;% raw %&#125; {% raw %} 和 {% endraw %}&#123;% endraw %&#125; 来包围

如果出现了 `Liquid Exception: Unknown tag 'endraw' in _posts`这样的问题， 使用`&#123;`代替 {，使用`&#125;`代替 }

