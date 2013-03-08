---
layout: post
title: 使用GitHub搭建个人博客
category: GitHub
---

GitHub允许大家在GitHub上创建自己的博客网站或主页，而且免费，不限流量，还可以绑定自己的域名，因此利用GitHub搭建个人主页是个不错的选择。网上有很多使用GitHub搭建个人博客的文章，使用google搜索"github 博客"可以找到很多相应的介绍，譬如下面两个是我读过的:

* <http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html>
* <http://pchou.info> - 里面有搭建博客的系列文章

我的工作机为Mac OS X 10.8，本文主要是从我的角度介绍最基本的入门几步。

#### What is Git?

Git是一个分布式源代码版本控制管理软件，类似的源码管理软件有CVS, Subversion等，Git由Linux大牛Linus Torvalds创立，目前被广泛用于open source项目的管理。Git相比svn有如下一些非常好的优点:

* Git提供了本地代码库，用户可以先在本地开发代码并提交到本地代码库，等到修改完成时再与远程代码库同步，因此降低了网络需求
* Git的fork and pull模式方便了code review, SVN并不自带code review功能，如果需要做code review，通常需要一个第三方软件来做，譬如用code collaborator，利用Git的fork and pull很容易做，因此Git非常适合管理Open Source项目，contributor可以将自己的改动送给project owner，由project owner review后merge到Git repo里

关于Git的详细介绍请参考:

* <http://git-scm.com/book> - Git英文版手册，非常好的文档
* <http://www.progit.org/book/zh> - Git中文版手册，是上面英文版的翻译

#### 在Mac上安装Git

按照<http://git-scm.com/book/en/Getting-Started-Installing-Git>的说明，下载了Git OS X installer，我下载的是 <mark>git-1.8.1.3-intel-universal-snow-leopard.dmg</mark>, 双击dmg文件后按照提示一步步next即可安装成功.

接下来需要做 first-time git setup，<http://git-scm.com/book/en/Getting-Started-First-Time-Git-Setup>有 git config 的详细说明.

#### GitHub

GitHub 是一个商业公司，提供源代码托管服务，使用Git实现版本控制。GitHub网站使用Ruby on Rails编写而成。GitHub同时提供付费账户和为开源项目提供的免费账户，免费帐户托管的项目都是public的，目前非常多的open source项目都托管在GitHub。

GitHub 号称是程序员的Facebook，不仅为程序员提供了免费源代码托管空间，还为程序员提供了一个社交平台，在GitHub有多种和别人的互动方式，可以fork别人的项目后提交pull request贡献自己的代码，可以watch某个人或某个项目，等等。

* <http://www.yangzhiping.com/tech/github.html> - 如果高效利用GitHub，整理了一些很有用的文章

#### GitHub Pages

GitHub上托管的每个项目都有一个主页，列出项目的源文件，可读性不太好，因此，github就设计了Pages功能，允许用户自定义项目首页，用来替代默认的源码列表。所以，github Pages可以被认为是用户编写的、托管在github上的静态网页。下面是GitHub Pages 官方文档:

* <http://help.github.com/pages>

GitHub提供两种类型的主页(<https://help.github.com/articles/user-organization-and-project-pages>):

* 个人或组织主页 - 页面内容位于 master 下
* 项目主页 - 页面内容位于 branch gh-pages 分支下，我们一般创建的都是项目主页

GitHub Pages支持Jekyll，用户push到GitHub库的静态页面都会经过Jekyll模板引擎的处理。

#### What is Jekyll?

jekyll基于Ruby，是一种静态页面转换引擎，是模板引擎liquid的扩展。jekyll的文档: 

* <http://jekyllbootstrap.com/lessons/jekyll-introduction.html> - 页面里还link一些其他更详细的文档

与asp、jsp、等动态页面语言不同的是，jekyll对模板的解析仅仅只有一次，它的目标就是将模板一次性的转化成静态网站。

#### 创建一个简单的blog

