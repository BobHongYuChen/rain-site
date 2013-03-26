---
layout: post
title: 使用GitHub搭建个人博客(4)Markdown里的字符转义
category: GitHub
---

使用md写blog时在输出某些字符时需要做转义，markdown文档在变成internet上可以访问的html之前经过了下面几步:

1. 处理jekyll/liquid语法，<mark>&#123;{ something }}, &#123;% something %}</mark> 会被当作jekyll语法处理
2. 按照markdown语法将内容翻译成html tag的内容

html也有特殊字符需要转义，因此在markdown文档里需要注意3种类型的字符转义。

###### jekyll特殊字符转义

* &#123;&#123; -----> &#38;#123;{
* &#123;% -----> &#38;#123;%

###### html特殊字符转义

html有5个特殊字符，不过只有下面两个必须做转义:

* &lt; -----> &amp;lt; or &amp;#60;
* &amp; -----> &amp;amp; or &amp;#38;

关于html字符转义可以参考 [wikipedia](http://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references#Predefined_entities_in_XML)

<p class="info">所有字符都可以做html转义，其转义后为: &amp;# + 字符的unicode编码 + 分号</p>

###### markdown特殊字符转义

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