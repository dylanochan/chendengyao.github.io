---
layout: post
title: "使用Git连接Github Page仓库搭建Jekyll博客"
author: "Dylano Chan"
categories: Git
tags: [Github]
image: gp1.jpg
---


如果你只需要搭建一个功能简单的博客，那么使用GitHub Page+Jekyll无疑是最省时省力的做法，但是网上许多教程都涉及到了ruby的使用还有众多的命令操作，这对新手来说极不友好。以下教程只需要了解一些简单的Git命令便可以搭建出一个博客。作为参考，这是我用Github搭建的[Github Page博客](https://chendengyao.github.io/)。
### 前置工作
* 创建Github账号
* 下载Git
### 开通Github Pages
* 创建GitHub Page仓库
<img src="{{ site.github.url }}/assets/img/gp1.png">
* 开启Github Page
<img src="{{ site.github.url }}/assets/img/gp2.png">
<img src="{{ site.github.url }}/assets/img/gp3.png">
* 创建index.html测试
<img src="{{ site.github.url }}/assets/img/gp4.png">
<img src="{{ site.github.url }}/assets/img/gp5.png">
在浏览器中输入https://你的用户名.github.io/  例如我应该输入https://chendengyao.github.io/
如果能出现你刚才输入的内容则开启GitHub Pages成功
### 用Git连接Github Page仓库
* 新建一个文件夹作为你的本地仓库（随便在哪里新建），右键然后点击Git Bash
* 设置用户名和邮箱(--global 为全局参数，表明本地所有Git仓库都会使用这个配置，注意用户名和邮箱要换成自己的)
* 
```git config --global user.name "chendengyao"```

```git config --global user.email "chendengyao@qq.com"```
* 生成密钥(SSH key)
  
```ssh-keygen -t rsa -C "chendengyao@qq.com"```
<img src="{{ site.github.url }}/assets/img/gp6.png">
注意记一下密匙的路径
* 添加密钥 将上一步骤生成的密钥即.ssh/id_rsa.pub中内容全部复制。在github的 Settings-->SSH and GPG keys-->New SSH key，key中粘贴复制的内容(Title自定义)
在Git Bash中输入```ssh -T git@github.com```
出现以下提示则为成功<img src="{{ site.github.url }}/assets/img/gp7.png">
* Git Bash中输入```git init ``` 初始化版本库
* 连接远程仓库 ```git remote add origin https://github.com/yourName/repositoryname.git```<img src="{{ site.github.url }}/assets/img/gp8.png">
### 下载Jekyll主题
*进入[Jekyll 主题网站](http://jekyllthemes.org/)找一个自己喜欢的主题，我的示例为[Jekyll](http://jekyllthemes.org/themes/lagrange/)<img src="{{ site.github.url }}/assets/img/gp8.png">然后会进入主题的GitHub，按照前面的方法获取仓库链接。
*进入Git Bash 输入``` git clone https://github.com/LeNPaul/Lagrange.git"将它克隆到本地。
### 将Jekyll推送到Github Page库
* 进入Git Bash，从远程仓库拉取文件(若远程仓库没有文件，直接执行下一步)
* 将本地文件push到远程仓库

```git status　```    查看工作目录的状态

```git add .```    将文件添加到暂存区

```git commit -m "commnet"```    提交更改,添加备注信息(此时将暂存区的信息提交到本地仓库)

```git push origin master```    将本地仓库的文件push到远程仓库(若 push 不成功，可加 -f 进行强推操作)
**接着进入前面说的链接，例如我是https://chendengyao.github.io/看看吧**
如果要修改删除或者添加库中的内容，则将文件夹中的内容修改删除或添加后重复以上push的步骤即可
### 注意事项
* 文章中涉及用户名或者邮箱的操作注意替换成自己的
* 如果需要对网站进行个人的修改，Jekyll提供了很详细的[文档](http://jekyllcn.com/docs/home/)
* 如果遇到问题，欢迎访问[我的博客](https://chendengyao.github.io/),里面提供了我的联系方式，欢迎一起交流。


