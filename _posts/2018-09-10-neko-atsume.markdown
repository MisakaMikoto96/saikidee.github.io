---
layout: post
title: 无聊的肥宅反编译neko atsume猫咪后院
date: '2018-09-10 15:43:19 +0800'
categories: 划水日常
published: true
---
![这里写图片描述](https://img-blog.csdn.net/20180910152738814?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

作为neko atsume的脑残宅粉，本人最大的兴趣之一就是每天云养猫，吃饭在养，睡前在养，走路在养，写作业在养，蹲lab在养，到考试前夕了还在养。没想到自己会对放置play这么有热情的，每当心态凉凉的时候就想点开app看一眼我的喵们>.<。图鉴类的游戏往往能够抓住收集爱好者和强迫症患者的心，就像盖满章的手册一样，安全感指数级增长pupupu！
![这里写图片描述](https://img-blog.csdn.net/20180910154445474?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 
鉴于一直搜集不全mementos，很想扒一扒得到mementos的内在规律，那么今天我们就来说一说（水一水）猫咪后院的反编译！

## 这里我们要用到的工具有：
1.	Apktool（我使用的是version2.3.2）
2.	dex2jar
3.	jd-gui



## Apktool的安装
建议用Homebrew来管理mac上的软件包，apktool官网的下载方式麻烦死了，用这个会比官网的下载方式要方便非常多！
运行terminal，输入：
```python
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null
```
 
![这里写图片描述](https://img-blog.csdn.net/20180910153759477?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
在password处输开机密码，等待完成。安装成功homebrew之后会出现一个successful的提示！


![这里写图片描述](https://img-blog.csdn.net/20180910153823685?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 
输入：
```python
brew install apktool
```
安装成功之后就可以查看你的apktool的版本、信息和使用方法了>.<


输入：
 ![这里写图片描述](https://img-blog.csdn.net/20180910153902431?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

反编译成功后，得到一个这样的文件：

![这里写图片描述](https://img-blog.csdn.net/20180910154017765?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 
 ![这里写图片描述](https://img-blog.csdn.net/20180910154042343?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 
（打开它！）
（Res包里是一些资源，图标、壁纸什么的都在里面kkk）
将这个文件夹右键重命名改成zip的后缀，再解压，会多生成一个名为 classes.dex的文件，直接拖进小黑屋，啊不对，终端，获取路径。



##二．Dex2jar
 https://github.com/pxb1988/dex2jar 

输入：
```python
	cd xxx/xxx/dex2jar
```
进入下载的dex2jar文件夹中 
注意修改一下这两个文件的可读性：
![这里写图片描述](https://img-blog.csdn.net/20180910154120368?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 
输入：
```python
chmod +x /Users/apple/Desktop/dex2jar-2.0/d2j_invoke.sh /Users/apple/Desktop/dex2jar-2.0/d2j-dex2jar.sh
```


输入： 
```python
sudo sh /Users/apple/Desktop/dex2jar-2.0/d2j-dex2jar.sh/Users/apple/Desktop/dex2jar2.0/classes.dex
```
这是classes.dex的路径 我放在dex2jar文件夹里了） 
进行反编译classes.dex文件，操作完成后，会在dex2jar文件夹中生成一个classes-dex2jar.jar文件。

![这里写图片描述](https://img-blog.csdn.net/20180910154143534?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70) 

##三．JD-GUI
下载链接：http://jd.benow.ca/ 
接下来我们需要用JD-GUI来呈现，注意一下这边下载的jdk版本是1.8.0 因为JD-GUI比较傲娇用java1.9打不开orz。
下载好JD-GUI之后我们打开它，右键显示包内容，调出它的脚本文件。

 ![这里写图片描述](https://img-blog.csdn.net/20180910154220176?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NhaWtpZGVl/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
 
可以用sublime打开，在257行加入：
```python
JAVACMD="/Library/Java/JavaVirtualMachines/jdk1.8.0_171.jdk/Contents/Home/bin/java"
```
然后保存关闭，就可以顺利运行JD-GUI了www 哦呼






















































































































































































































































































































































