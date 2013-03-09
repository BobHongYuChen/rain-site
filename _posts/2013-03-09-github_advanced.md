---
layout: post
title: 使用GitHub搭建个人博客之进阶设定
category: GitHub
---

经过上一篇的介绍，我们已经在GitHub上搭建了一个最简单的blog，接下来我们介绍一些进阶设定。

#### 绑定域名

https://help.github.com/articles/setting-up-a-custom-domain-with-pages

#### Install Jekyll

你可以不在本机安装jekyll，但为了在上传文件到GitHub前能在本地看一下效果，强烈建议你在本机安装jekyll。个人体会，因为jekyll只支持UTF8编码，我从原来的wiki里copy文档时常有编码不对的问题，另外我对jekyll语法不熟悉，常会写错，还有，我是自己写了一个template，因此也需要时时看到效果，因此，本地的kekyll环境对我是非常重要的。

1. install Ruby

<http://www.hoowolf.net/2012/03/29/installing-ruby-on-rails-on-mac-os-x-lion>

    $ rvm install 1.9.3

Error running 'make', please read /Users/rainz/.rvm/log/ruby-1.9.3-p392/make.log
There has been an error while running make. Halting the installation.

st.c:520:35: error: implicit conversion loses integer precision: 'st_index_t' (aka 'unsigned long') to 'int'

    $ export CC=gcc


2. install jekyll

http://equation85.github.com/blog/install-jekyll-on-mac/
https://github.com/mojombo/jekyll/wiki/Install
http://brandonbohling.com/2011/08/27/Installing-Jekyll-on-Mac/

3. have a try

go to the dir "~/Documents/gitroot/rain-site"
run "jekyll --server"
type http://localhost:4000/index.html in your browser

#### 创建模板

一个简单的办法是找一个现成的模板，在 <https://github.com/mojombo/jekyll/wiki/Sites> 列出了很多，你可以从中选择一个，我看了一下发现没有满意的模板，因此决定自己做一个。

如果你对jekyll已经比较了解，做一个简单的模板还是比较容易的，不了解jekyll的可以仔细看一下文档: <http://jekyllbootstrap.com/lessons/jekyll-introduction.html>,了解jekyll以后定义模板的主要工作其实就是CSS和UI设计了，我找了一个现成的CSS库 <http://ink.sapo.pt/index.php>, ink非常好用，CSS很清爽，这里推荐一下。
