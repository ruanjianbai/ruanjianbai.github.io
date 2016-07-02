---
layout: post
title: "关于SSH KEY 以及管理多个 SSH KEY"
date: 2016-06-21 17:01:18 +0800
comments: true
categories: Android
---
##关于SSH KEY

通常我们使用 SSH 协议来访问 Git 仓库，获得所有仓库的读写权限，这样每次操作都不需要再输入账号和密码了。

关于SSH协议可参考中文维基百科 (http://zh.wikipedia.org/zh/Secure_Shell) 

目前主流的代码托管平台，比如Github，是一个仓库可以有多个公钥，但一个公钥只能认证一个用户，但一个用户可以拥有多个公钥。

###生成SSH KEY
打开终端，输入ssh-keygen -t rsa -C “username@example.com”,( 注册的邮箱)，接下来点击enter键即可（也可以输入密码）

{% codeblock lang:bash%}
➜  ~ ssh-keygen -t rsa -C bailu@doumob.com
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/bailu/.ssh/id_rsa): 
/Users/bailu/.ssh/id_rsa_codingnet
{% endcodeblock %}

成功之后
{% codeblock lang:bash%}
Your identification has been saved in /Users/bailu/.ssh/id_rsa_codingnet.
Your public key has been saved in /Users/bailu/.ssh/id_rsa_codingnet.pub.
The key fingerprint is:
SHA256:NB+nvyQErZft02UwWmDl5foQrdDye70qHNmP0NxRPjU bailu@doumob.com
{% endcodeblock %}

注意：`/Users/bailu/.ssh/id_rsa_codingnet`为设定的私钥文件路径和名称，`id_rsa_codingnet.pub`为公钥，文件名称根据不同代码托管平台起不同的名称，已示区分，可以管理多个KEY

然后
{% codeblock lang:bash%}
cd ~/.ssh
cat id_rsa.pub
{% endcodeblock %}
<!--more-->
###添加公钥
复制公钥内容粘贴到托管平台账户的SSH公钥设置页面

###测试

SSH KEY 公钥添加成功后，输入
{% codeblock lang:bash%}
➜  ~ ssh -T git@git.coding.net
Warning: Permanently added the RSA host key for IP address '59.56.27.71' to the list of known hosts.
Hello doumob You've connected to Coding.net by SSH successfully!
{% endcodeblock %}

##管理多个 SSH KEY
当之前已经有了向github提交的SSH Key，则测试不成功

{% codeblock lang:bash%}
➜  ~ ssh -T git@git.coding.net
The authenticity of host 'git.coding.net (14.215.101.70)' can't be established.
RSA key fingerprint is SHA256:jok3FH7q5LJ6qvE7iPNehBgXRw51ErE77S0Dn+Vg/Ik.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'git.coding.net,14.215.101.70' (RSA) to the list of known hosts.
Permission denied (publickey).
{% endcodeblock %}

这时候需要修改配置文件
在 ~/.ssh 目录下新建一个config文件
添加内容：
{% codeblock  %}
{% raw %} # codingnet {% endraw %} 
Host git.coding.net
HostName git.coding.net
User bailu@doumob.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_codingnet

{% raw %}# github {% endraw %} 
Host github.com
HostName github.com
User ruanjianbai@gmail.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
{% endcodeblock %} 

添加私钥

{% codeblock lang:bash%}
➜  ~ ssh-add /Users/bailu/.ssh/id_rsa
➜  ~ ssh-add /Users/bailu/.ssh/id_rsa_codingnet
{% endcodeblock %}

可以通过 `ssh-add -l` 来确私钥列表

{% codeblock lang:bash%}

➜  ~ ssh-add -l

{% endcodeblock %}

再测试，则成功！


