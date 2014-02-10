.. title: 开始用 Nikola 写博客
.. slug: kai-shi-yong-nikola-xie-bo-ke
.. date: 2014/02/01 14:21:49
.. tags: python,nikola
.. link: 
.. description: 
.. type: text

====
源起
====

作为一个技术人，拥有一个自己的博客是必须的，可以用来记录自己学习笔记，
平时学习工作中遇到的问题的解决方法，发表对一些技术的看法和观点以及对人
生和生活的一些感悟。总之，博客是一个很好的平台，记录自己的成长，我希望
通过博客达到Record, Think, Summarize, Improve 的目的。

====
方案
====
----------
常见的方案
----------

常见的技术博客一般可以分为下面3类：现成的技术博客网站，用Web框架自己在
VPS上搭建动态博客，使用轻量级标记语言写静态博客

- Cnblogs,CSDN 等现成的技术博客平台
- Wordpress,RoR,Django,Flask 等搭建
- Jekyll,Octopress,Nikola,Peclian 等静态博客

其中用框架搭建动态博客最折腾；利用现成的博客平台最简单--注册帐号就可以
写博客，但通常而言不够灵活且一般只能在网页上编辑，对于 coder 而言，永远
是自己的本地编辑器最方便；现在越来越多的人从这两种方案转向第三种，使用
markdown,reStructured,org 等轻量标记语言写博客，然后直接上传到托管平台
或在本地用一些转换工具生成 html 文件再上传到托管平台，对于程序员，文本
文件永远是最透明的，管理起来也非常方便，尤其是借助版本控制器，更改同步
变得 So easy.

--------
我的选择
--------

在折腾过各种方案后，最终选择了用 Nikola 构建静态博客。尝试过在 Cnblog上
写，因为在网页上写起来不方便而放弃；也尝试过用 Flask 和 Webpy 等自己手
动搭建一个动态博客站点，因为太折腾而且最终功能和效果很不理想而放弃；
Jekyll 和 Octopress 是 Ruby Powered，没学过 Ruby 懒得折腾；Hyde 也用过，
还不错不过好久没更新了；Nikola 更新比较频繁开发很活跃，有许多 `插件`_
和 `主题`_ ，而且支持多国语言，所以选定了 Nikola，希望这是我的博客的最
终归属。

.. _`插件`: http://plugins.getnikola.com/
.. _`主题`: http://themes.getnikola.com/

===================
Nikola 安装使用方法
===================
----
安装
----
- Debian 下安装
  ::
     
     sudo apt-get install build-essential python-dev libxml2-dev libxslt1-dev python-pip
     pip install nikola requests webassets --user
  
- ArchLinux 下安装
  ::

     sudo pacman -S libxml2 libxslt python2-pip
     pip2 install nikola requests webassets --user

添加路径到环境变量 ``export PATH=$PATH:~/.local/bin`` 或者将其写入
*.bashrc* 文件中然后 ``source ~/.bashrc``

-----------
使用 Nikola
-----------
#. 生成博客站点目录
   
   ``nikola init myblogs`` 会生成项目的空目录和配置文件
  
#. 修改 myblogs/conf.py
   
   修改 *BLOG_AUTHOR*, *BLOG_TITLE* , *BLOG_EMAIL* , *BLOG_DESCRIPTION* 等相关变量
  
#. 在 myblogs 目录下新建博客
   
   ``nikola new_post`` 根据提示输入文章标题，会在 posts 目录下生成博客，  中文标题生成的博客文件名会自动转成拼音，这个功能相当赞。然后就是用你最喜欢的编辑器编辑posts 目录下的 .rst 或 .txt 或 .md 文件了。

#. 生成 html
   
   ``nikola build`` 会将 posts 目录下的标记文本转换成 html，生成的文件默认在 output 目录下
  
#. 本地预览
   
   ``nikola serve`` 然后用浏览器打开 http://127.0.0.1:8000
   也可以用 ``nikola serve -a 0.0.0.0 -p 8000`` 指定地址和端口

#. 上传 html 静态文件
  
   使用版本管理器将 output 目录下的文件上传到托管服务器即可
