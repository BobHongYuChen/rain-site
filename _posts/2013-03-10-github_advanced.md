---
layout: post
title: 使用GitHub搭建个人博客(3)绑定域名、创建模板等进阶设定
category: GitHub
---

经过上一篇的介绍，我们已经在GitHub上搭建了一个最简单的blog，接下来我们介绍一些进阶设定。

##### 1. 绑定域名

请参考 <https://help.github.com/articles/setting-up-a-custom-domain-with-pages>

##### 2. 创建模板

一个简单的办法是找一个现成的模板，在 <https://github.com/mojombo/jekyll/wiki/Sites> 列出了很多，你可以从中选择一个，我看了一下发现没有满意的模板，因此决定自己做一个。

如果你对jekyll已经比较了解，做一个简单的模板还是比较容易的，不了解jekyll的可以仔细看一下文档: <http://jekyllbootstrap.com/lessons/jekyll-introduction.html>,了解jekyll以后定义模板的主要工作其实就是CSS和UI设计了，我找了一个现成的CSS库 <http://ink.sapo.pt/index.php>, ink非常好用，CSS很清爽，这里推荐一下。下面是我的目录结构:

<pre class="prettyprint">
    site_root
        |- _includes
        |- _layouts
              |- default.html
        |- _posts
        |- css                   /* css folder is from ink library */
        |- font                  /* font folder is from ink library */
        |- google-code-prettify  /* from google code prettify */
        |- _config.yml
        |- CNAME
        |- index.html
</pre>

##### 3. 代码高亮

看了一些资料提到GitHub Pages代码高亮可以使用pygments或者gist，看了一些文档后还是没有完全理解，而且有人提到pygments有时不work，因此决定自己找一个方案，一者省得继续花时间了解pygments，二者对GitHub Pages减少依赖。

一般页面的语法高亮都是JavaScript实现的，搜索"javascript 语法高亮"可以找到很多实现，我使用的是[google code prettify](https://code.google.com/p/google-code-prettify)，步骤如下:

1. 下载 google code prettify
2. 将目录google-code-prettify放到站点根目录下，与\_layouts, \_posts平级（jekyll编译时会将非\_开头的folder copy到\_site目录下，因此下一步里可以使用/google-code-prettify/... 找到对应的js文件）
3. 在模板文件的header部分加上 <mark>&lt;script src="/google-code-prettify/run_prettify.js>&lt;/script></mark>
4. 将需要高亮的代码段放在pre or code tag里: <mark>&lt;pre class="prettyprint">...&lt;/pre> or &lt;code class="prettyprint">...&lt;/code></mark>

##### 4. Markdown里的字符转义

markdown文档在变成internet上可以访问的html之前经过了下面几步:

1. 处理jekyll/liquid语法，<mark>&#123;{ something }}, &#123;% something %}</mark> 会被当作jekyll语法处理
2. 按照markdown语法将内容翻译成html tag的内容

html也有特殊字符需要转义，因此在markdown文档里需要注意3种类型的字符转义。

###### 4.1 jekyll特殊字符转义

* &#123;&#123; -----> &#38;#123;{
* &#123;% -----> &#38;#123;%

###### 4.2 html特殊字符转义

html有5个特殊字符，不过只有下面两个必须做转义:

* &lt; -----> &amp;lt; or &amp;#60;
* &amp; -----> &amp;amp; or &amp;#38;

关于html字符转义可以参考 [wikipedia](http://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references#Predefined_entities_in_XML)

<p class="info">所有字符都可以做html转义，其转义后为: &amp;# + 字符的unicode编码 + 分号</p>

###### 4.3 markdown特殊字符转义

下列Markdown文本需要在前面加上 \ 转义:

<pre class="prettyprint">
\   反斜杆
`   backtick
*   星号
_   下划线
{}  花括弧
[]  方括弧
()  圆括弧
#   井号
+   加号
-   减号
.   点
!   感叹号
</pre>