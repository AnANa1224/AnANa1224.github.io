---
layout: post
title:  "搭建博客"
categories: me
tags:  An  
author: github 
---

* content
{:toc}


## 前言

一直就想搭建一个属于自己的博客网站，但是一直拖着没有执行，在一次偶然的机会看到了鸿洋大神的 [如何利用github打造博客专属域名](https://link.jianshu.com/?t=http://blog.csdn.net/lmj623565791/article/details/51319147)，就心血来潮，马上自己动手做了一个，耗时了近一个星期，终于差不多完成了，特意记录下来，供他人参考。

### 关于Jekyll

Jekyll 是一个免费的生成静态网页的工具，不需要数据库支持。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，可以配合第三方服务例如： Disqus（评论）、多说(评论) 以及分享 等等扩展功能，Jekyll 可以直接部署在 Github（国外） 或 Coding（国内） 上，可以绑定自己的域名。[Jekyll中文文档](https://link.jianshu.com/?t=http://jekyll.bootcss.com/)、[Jekyll英文文档](https://link.jianshu.com/?t=https://jekyllrb.com/)、[Jekyll主题列表](https://link.jianshu.com/?t=http://jekyllthemes.org/)。

### 关于GitHub Pages

官方说法是Websites for you and your projects.[GitHub Pages](https://link.jianshu.com/?t=https://pages.github.com/)是一个免费的静态网站托管平台，由github提供，它具有以下特点：

1. GitHub Pages 有 300M 免费空间，资料自己管理，保存可靠；
2. 学着用 GitHub，享受 GitHub 的便利，上面有很多大牛，眼界会开阔很多；
3. 顺便看看 GitHub 工作原理，最好的团队协作流程；
4. GitHub 是趋势；
5. 可以自定义域名

### 本地环境搭建

如果你只是想使用本主题，而不想搭建本地环境，那么可以直接跳过这部分，不搭建本地环境则不能实现本地预览，以下安装操作都是在Windows系统环境下进行。（安装有点烦，会出现你意想不到的错误，祝你好运！）

##### 安装Ruby

jekyll本身基于Ruby开发，因此，想要在本地构建一个测试环境需要具有Ruby的开发和运行环境。在windows下，可以使用[Rubyinstaller](https://link.jianshu.com/?t=http://rubyinstaller.org/downloads/)安装，[ruby安装官方说明](https://link.jianshu.com/?t=http://www.ruby-lang.org/zh_cn/downloads/)，Windows下只需要保持默认状态一路下一步就可以了。

##### 安装RubyDevKit

从这里[下载DevKit](https://link.jianshu.com/?t=http://rubyinstaller.org/downloads/)，注意版本要与Ruby版本一致。

下载下来的是一个sfx格式的文件，如果你安装有7-zip，可以直接双击，它会自解压到你所选择的目录。

解压完成之后，用cmd进入到刚才解压的目录下，运行下面命令，该命令会生成config.yml。

$ ruby dk.rb init

config.yml 文件实际上是检测系统安装的ruby的位置并记录在这个文件中，以便稍后使用。但上面的命令只针对使用rubyinstall安装的ruby有效，如果是其他方式安装的话，需要手动修改`config.yml`。

最后，执行如下命令，执行安装：

$ ruby setup.rb

如果没有setup.rb的话，执行：

$ ruby dk.rb install

##### 安装Git

[Git下载](https://link.jianshu.com/?t=https://git-scm.com/downloads/)

创建本地仓库myblog

$ git init myblog

##### 安装Bundler

建议使用[Bundler](https://link.jianshu.com/?t=http://bundler.io/)来安装和运行Jekyll。

直接使用下面命令即可：

$ gem install bundler

然后在上面的myblog目录创建一个叫Gemfile的文件，注意没有后缀，输入

source 'https://ruby.taobao.org/'
gem 'github-pages', group: :jekyll_plugins

保存后，在命令行中执行

$ bundle install

命令会根据当前目录下的Gemfile，安装所需要的所有软件。这一步所安装的东西，可以说跟github本身的环境是完全一致的，所以可以确保本地如果没有错误，上传后也不会有错误。而且可以在将来使用下面命令，随时更新环境，十分方便

$ bundle update

使用下面命令，启动转化和本地服务：

$ bundle exec jekyll serve

在浏览器里输入： [http://localhost:4000](https://link.jianshu.com/?t=http://localhost:4000)，就可以看到你的博客效果了。

### 部署到服务器

我这里讲的是部署到 Github Page 创建一个 github 账号，然后创建一个跟你账户名一样的仓库，如我的 github 账户名叫[skylarklxlong](https://link.jianshu.com/?t=https://github.com/skylarklxlong) ，我的 github 仓库名就叫 [skylarklxlong.github.io](https://link.jianshu.com/?t=https://github.com/skylarklxlong/skylarklxlong.github.io)，创建好了之后，把刚才建立的 myblog 项目 push 到 username.github.io仓库里去（username指的是你的github用户名），检查你远端仓库已经跟你本地 myBlog 同步了，然后你在浏览器里输入 username.github.io ，就可以访问你的博客了。

### 编写文章

所有的文章都是 _posts 目录下面，文章格式为 mardown 格式，文章文件名可以是 .mardown 或者 .md。

编写一篇新文章很简单，你可以直接从 _posts/ 目录下复制一份出来 `2019-10-14-welcome-to-myblog.md` ，修改名字为 2019-10-14-article1.markdown ，注意：文章名的格式前面必须为 2019-10-14- ，日期可以修改，但必须为 年-月-日- 格式，后面的 article1 是整个文章的连接 URL，如果文章名为中文，那么文章的连接URL就会变成这样的：%E6%90%AD%E5， 所以建议文章名最好是英文的或者阿拉伯数字。 双击 2019-10-14-article1.markdown 打开

layout: post
title: 欢迎来到我的博客
date: 2019-10-14
tags: Jekyll

title: 显示的文章名， 如：title: 我的第一篇文章
date: 显示的文章发布日期，如：date: 2019-10-14
tags: tag标签的分类，如：tags: 随笔

注意：文章头部格式必须为上面的，.... 就是文章的正文内容。

我写文章使用的是 MarkdownPad2 编辑器，如果你对 markdown 语法不熟悉的话，可以在网上查找写资料，后续我也会写关于如何使用markdown的相关文章。

### 使用我的模版

虽然博客部署完成了，你会发现博客太简单不是你想要的，如果你喜欢我的模板的话，可以使用我的模板。

首先你要获取的我博客，[Github项目地址](https://link.jianshu.com/?t=https://github.com/skylarklxlong/skylarklxlong.github.io.git)，你可以直接[点击下载博客](https://link.jianshu.com/?t=https://github.com/skylarklxlong/skylarklxlong.github.io/archive/master.zip)，进去skylarklxlong.github.io/ 目录下， 使用命令部署本地服务

​	$ jekyll server  

就可以看到的博客样式了。

### 修改成你自己的博客

1. 如果你想使用我的模板请把 _posts/ 目录下的文章都去掉。

2. 修改 _config.yml 文件里面的内容为你自己的。

然后使用 git push 到你自己的仓库里面去，检查你远端仓库，在浏览器输入 username.github.io 就会发现，你有一个漂亮的主题模板了。

## 使用模板搭建博客

1. 创建GitHub账号
2. 创建一个库
3. 找到一个博客模板
4. 进入此博客模板GitHub页面
5. 点击fork到自己建的库中
6. 修改自己喜欢的域名
7. 建一个文件夹并进入
8. 进入终端,执行命令
   1. git clone 自己库的url
   2. git push -u origin master
9. 详读模板配置信息,修改配置,使之变成自己的东西
