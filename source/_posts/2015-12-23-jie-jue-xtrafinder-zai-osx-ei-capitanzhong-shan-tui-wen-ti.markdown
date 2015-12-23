---
layout: post
title: "解决XtraFinder 在OSX EI Capitan中闪退问题"
date: 2015-12-23 11:57:28 +0800
comments: true
categories: mac
---
#关于OSX 10.11系统完整保护（System Integrity Protection 后面简称SIP）
SIP阻止代码注入（code injection）以及很多其他事等

XtraFinder通过代码注入到Finder应用进程来工作

#如何让XtraFinder在OSX 10.11上可以正常使用
你需要部分（partially）禁止SIP（译注：启用SIP，关闭debug）

并不建议完全禁止SIP，这样会让你的电脑安全性降低

#如何部分禁止SIP
1. 通过重启并且按住Common+R键进入Recovery界面
2. 启动顶部工具栏上的终端（terminal）
3. 输入命令如下命令然后再重启

{% codeblock %}
csrutil enable --without debug
{% endcodeblock %}

#命令行csrutil enable --without debug做了什么
它允许代码注入 

这意味着XtraFinder能注入它的代码到Finder应用进程中

#如何恢复SIP到原始状态
进入系统Recovery并在终端输入如下命令：

{% codeblock %}
csrutil clear
{% endcodeblock %}



本文内容翻译自XtraFinder官方文章：http://www.trankynam.com/xtrafinder/sip.html