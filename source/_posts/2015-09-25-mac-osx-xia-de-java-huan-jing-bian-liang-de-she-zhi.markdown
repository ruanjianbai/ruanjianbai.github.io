---
layout: post
title: "Mac 中配置 java 环境"
date: 2015-09-25 12:13:30 +0800
comments: true
categories: Mac
---
目前的mac osx 下默认是没有安装java的，

###通常安装jdk有三种方法：
1.在terminal下输入java，然后根据提示去下载苹果官方的openJdk进行安装, 但目前的版本只有1.6的（随着Android 5.0 默认需要使用jdk1.7，该版本已经无法满足我们的需求了）

2.手动去oracle官网下载比较新的jdk版本进行安装

3.在终端执行brew-cask install java，自动安装好最新的java环境（该方法的前提是你要安装有brew-cask,有空再说该工具，先忍住不说）

###设置环境变量
	
	$ vim .bash_profile 

	export JAVA_HOME=$(/usr/libexec/java_home)
	
	export PATH=${JAVA_HOME}/bin:$PATH

	$ source .bash_profile

	$ echo $JAVA_HOME
	/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home
	
###查看机器安装了哪些版本的jdk
	$ /usr/libexec/java_home -V
	Matching Java Virtual Machines (3):
    1.8.0_51, x86_64:	"Java SE 8"	/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/ Home
    1.6.0_65-b14-468, x86_64:	"Java SE 6"	/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
    1.6.0_65-b14-468, i386:	"Java SE 6"	/Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
  
 此时我的电脑上安装了三个版本的jdk，默认使用最新的版本
 	
 	$ java -version
 	java version "1.8.0_51"
	Java(TM) SE Runtime Environment (build 1.8.0_51-b16)
	Java HotSpot(TM) 64-Bit Server VM (build 25.51-b03, mixed mode)
	
如果想切换到jdk1.6,则需要这样设置

	$ vim .bash_profile 
	export JAVA_HOME=$(/usr/libexec/java_home -v 1.6)
	
	$ source .bash_profile
	
此时，再查看

	$ java -version
	java version "1.6.0_65"
	Java(TM) SE Runtime Environment (build 1.6.0_65-b14-468-11M4828a)
	Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-468, mixed mode)
	
=======
目前的 MAC OSX 下默认是没有安装 Java 的，

###通常安装jdk有三种方法：
1.在 terminal 下输入`java`，然后根据提示去下载苹果官方的 openJdk 进行安装, 但目前的版本只有1.6的（随着Android 5.0 默认需要使用 jdk1.7 ，该版本已经无法满足我们的需求了）

2.手动去 oracle 官网下载比较新的 jdk 版本进行安装

3.在终端执行`brew-cask install java`，自动安装好最新的 java 环境（该方法的前提是你要安装有 brew-cask ,有空再说该工具，先忍住不说）

###设置环境变量
{% codeblock lang:bash  %}
$ vim .bash_profile 

export JAVA_HOME=$(/usr/libexec/java_home)
	
export PATH=${JAVA_HOME}/bin:$PATH

$ source .bash_profile

$ echo $JAVA_HOME
/Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/Home
{% endcodeblock %}
<!--more-->
###查看机器安装了哪些版本的jdk
{% codeblock lang:bash %}
$ /usr/libexec/java_home -V
Matching Java Virtual Machines (3):
1.8.0_51, x86_64:"Java SE 8" /Library/Java/JavaVirtualMachines/jdk1.8.0_51.jdk/Contents/ Home
1.6.0_65-b14-468, x86_64:"Java SE 6" /Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
1.6.0_65-b14-468,i386:"Java SE 6" /Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home
{% endcodeblock %} 
此时我的电脑上安装了三个版本的 jdk ，默认使用最新的版本
{% codeblock lang:bash %}
$ java -version
java version "1.8.0_51"
Java(TM) SE Runtime Environment (build 1.8.0_51-b16)
Java HotSpot(TM) 64-Bit Server VM (build 25.51-b03, mixed mode)
{% endcodeblock %}		
如果想切换到 jdk1.6 ,则需要这样设置
{% codeblock lang:bash %}
$ vim .bash_profile 
export JAVA_HOME=$(/usr/libexec/java_home -v 1.6)
$ source .bash_profile
{% endcodeblock %} 
	
	
此时，再查看
{% codeblock lang:bash %}
$ java -version
java version "1.6.0_65"
Java(TM) SE Runtime Environment (build 1.6.0_65-b14-468-11M4828a)
Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-468, mixed mode)
{% endcodeblock %} 	



