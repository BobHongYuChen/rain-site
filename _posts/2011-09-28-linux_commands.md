---
layout: post
title: Linux常用命令
category: linux_and_mac
---

###### 基本命令

<pre class="prettyprint">
man xxx  //显示命令xxx的帮助手册
pwd      //显示当前工作目录 
sudo xxx //以root身份执行命令xxx
ls      //列出目录内容
  ls -l   //表示long format，与命令ll效果相同
  ls -a   //列出所有文件，包括隐藏文件
cp -a   //复制所有目录并包含子目录
mv      //移动/重命名
  mv abc.zip def.zip   //重命名abc.zip为def.zip
  mv abc.zip /tmp      //将当前目录下的文件abc.zip移动到目录/tmp下
rm -rf   //删除非空目录，包括目录下所有文件和子目录
rmdir    //删除空目录
</pre>

###### 显示文件内容

<pre class="prettyprint">
cat    //显示文件内容
more   //分页显示文件内容
less   //与more相似，具有更高交互能力
head /opt/temp/tomcat.log     //显示文件的前10行
head -3 /opt/temp/tomcat.log  //显示文件的前3行
tail /opt/temp/tomcat.log     //显示文件的最后10行
tail -f /opt/temp/tomcat.log  //显示文件的最后10行，并随着文件变化及时更新，这个命令通常用于监控日志文件
</pre>

###### 目录搜索与文字搜索

<pre class="prettyprint">
find / -name test    //在根目录下搜索名字为“test”的目录或文件
find / -name test\*  //在根目录下搜索名字以“test”开头的目录或文件
locate test    //搜索名字为“test”的目录或文件，相比find命令，locate是基于数据库查询，查询更快，但可能不是实时的数据
locate test\*  //搜索名字以“test”开头的目录或文件
whereis   //只搜索源代码。二进制文件或是帮助文件
which     //只在环境变量$PATH指定的目录里查询
grep -n "Hello World" /tmp/a.txt  //在a.txt里查找字符“Hello World”并显示行号
</pre>

###### 权限相关命令

每个linux文件都具有4种权限：可读（r），可写（w），可执行（x）和无权限（-）。可以通过 *ls -l* 命令查看该文件或目录的使用权限，权限由10个字符组成，如下： 

<table class="ink-table ink-bordered">
  <tbody>
    <tr><td>字符</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td><td>10</td></tr>
    <tr><td>字母值</td><td>-</td><td>r</td><td>w</td><td>x</td><td>r</td><td>w</td><td>x</td><td>r</td><td>w</td><td>x</td></tr>
    <tr><td>对应数字值</td><td>-</td><td>4</td><td>2</td><td>1</td><td>4</td><td>2</td><td>1</td><td>4</td><td>2</td><td>1</td></tr>
    <tr><td> </td><td>'d'表示是目录，<br> '-'表示是文件，<br> 'l'表示是链接文件 </td><td colspan="3">owner的权限 </td><td colspan="3">group的权限 </td><td colspan="3">其他用户的权限</td></tr>
  </tbody>
</table>

命令列表:

<pre class="prettyprint">
chmod 777 /tmp/abc.zip   //将文件abc.zip的权限改成最大 
chown rain /tmp/abc.zip  //将文件abc.zip的owner改成rain
chown rain:users /tmp/abc.zip  //将文件abc.zip的owner改成rain,组改成users 
chgrp users /tmp/abc.zip  //将文件abc.zip的组改成users
</pre>

###### IO重导与管道命令

* &#62; － 输出重导
* &#62;&#62; - 附加输出重导，当目标文件已经存在时，不会覆盖原有内容，重导内容会附加在原有文件之后
* &lt; － 输入重导
* &lt;&lt; - 附加输入重导
* | - Pipe管道命令，把一个命令的输出直接作为另一个命令的输入

<pre class="prettyprint">
cat > /tmp/editor.txt //利用cat命令和输出重导可以组成简单的文字编辑器，CTRL-C 可以结束输入
ps aux|grep wbx       //列出含有wbx字样的进程
</pre>

###### 磁盘与内存使用情况

<pre class="prettyprint">
du  //显示当前目录下所有子目录所占空间大小（不显示文件大小），侧重显示目录树下某个目录的大小
du -sh /tmp  //显示/tmp目录所占空间大小, s表示仅显示总计, h表示显示大小时使用单位K,M,G
df    //显示磁盘相关信息，侧重列出分区后每个分区的使用情况
free  //检查内存状态
</pre>

###### 用户管理命令

<pre class="prettyprint">
passwd  //改变自己的密码
passwd rain  //改变rain的密码
whoami  //显示自身的用户名称
who     //列出登录用户信息
finger  //列出登录用户信息
useradd //增加用户
useradd -d /opt/rain -g users rain  //增加用户rain，主目录是/opt/rain，属于组users
groupadd users  //增加组users
write root   //给root用户发送信息，CTRL-C可以退出信息输入
</pre>

###### 进程控制与管理

Linux进程分为两种，前台进程或后台进程，后台进程的服务名通常以“d”结尾。系统服务通常是后台进程，用户利用“&amp;”来处理的进程也是后台进程。 

<pre class="prettyprint">
ps -x    //查看所有进程
ps -aux  //查看所有进程
ps -x | grep wbx  //列出含有wbx字样的进程
kill 4687 4688  //终止4687和4688两个进程
kill -9 4687    //强行终止4687进程
kill -HUP 4687  //对某个Daemon修改或设置后，使用-HUP（Hang Up）参数重新启动该进程
top    //显示进程，以使用CPU时间排序，会定时更新
</pre>

###### Reference: 

* <http://linux.chinaitlab.com/special/linuxcom> - linux常用命令全集
* <http://www.yesky.com/20030306/1655486.shtml> - Linux入门常用命令