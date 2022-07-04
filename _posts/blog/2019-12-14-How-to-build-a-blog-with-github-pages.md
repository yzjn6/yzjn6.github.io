---

layout: post
title: 如何在Windows平台上基于github搭建个人博客平台
categories: Blog
description: 从零开始学习和搭建个人博客平台
keywords: github，博客搭建，github.io

---

- 本文将介绍在Windows平台上搭建基于github pages 的个人博客网站的过程，以及利用Jekyll进行本地博客调试的过程，对于不懂前端的人来说是一个比较基础的入门教程。

- 本文基于知乎答主沙漏文章[《如何在Windows平台上基于github搭建个人博客平台》](https://zhuanlan.zhihu.com/p/102346113)修改

## 简介

一直以来想建一个个人博客，还申请了域名，至于服务器这个玩意，说贵吧，多吃几天泡面还能买得起，说便宜吧，买一下还得想好久，就怕买了玩几天搁那闲放着，没啥意义浪费钱，再便宜也怕浪费。最近在B站学JS，评论区有一个问问题的，发了一个JS链接，意思是他照着视频敲了代码却没效果，我注意到他的域名也是'.xyz'结尾，心想跟我一样都是买便宜域名，是不是他还有便宜服务器？于是查了一下他的域名指向的IP地址。？？？居然是指向GitHub。。去知乎上一搜，找到沙漏大佬的文章，才发现Github Page的强大功能。

Github Page提供免费的静态站点托管服务，因此可以用Jekyll搭建一个静态的网站，因为是静态的，所以不支持在线写，需要在本地写好后上传到Github的仓库中。不要以为这会很麻烦，我们写文章只需要写Markdown就可以了，Jekyll可以通过设定好的格式帮你快速生成相应的Html文章。

## 一. Markdown 简介

### 1. 语法简介

可参考我的另一篇文章[Markdown的基本语法](https://chauby.github.io/2019/12/13/markdown-basic-skills/)

### 2. Markdown编辑器Typora

为了方便写Markdown，我们需要一个Markdown的解释器来实时预览写出来的效果。市面上有很多支持Markdown语法的代码编辑器可选，例如vscode，sublime text，atom等等。我选择的是一款目前还处于beta阶段的Markdown编辑器[Typora](https://www.Typora.io)，与传统的分两栏写markdown和预览markdown文件不同的是，Typora能够“所见即所得”，写完了就可以实时在当前位置看到最终效果。而且Typora本身支持内嵌LaTex数学公式，本人试过，几乎所有的公式都可以嵌入，而且支持公式的自动编号，可以作为平时快速写作的一个高效编辑器。这里不仔细讲Typora的用法，网上可以找到许多教程，例如[Typora完全使用详解](https://sspai.com/post/54912)，有兴趣的朋友可以了解一下。

## 二. 基于Github的博客搭建

### 1. 创建博客仓库

#### 1.1 Github代码仓库简介

[Github](https://github.com)是一个在线的代码托管平台，支持使用git进行代码的版本管理，用户可以自由注册和将自己的代码托管到远程的Github仓库上，然后随时随地可以下载使用。这里不对Github的使用做深入的解释，感兴趣的人可以自行搜索。这里假设阅读本文的人已经对Github的使用有了一定的了解。本人的这个博客其实就是一个托管在Github仓库上的代码仓库，github提供了种特殊的repo，允许用户简单地创建自己的博客网页。

#### 1.2 创建Repo

在自己的Github上新建一个repository，这里注意，跟普通的代码仓库不一样，我们要创建一种特殊的repository，仓库的名字只能取为你的github用户名.github.io，例如我的用户名叫chauby，那么我的这个仓库名字就只能取chauby.github.io。如下图所示，由于我已经有这样一个仓库了，所以提醒我有错误：

<center>
    <img src="/images/posts/blog/github_new_repo.png" alt="picture not found" style="zoom:100%;" />
    <br>
</center>

然后点击下面绿色的"Create repository"，仓库就创建好了。然后我们创建好的博客的首页地址就是 https://yourname.github.io，这里yourname就是你的github账户名字。

仓库创建好了以后还不行，还需要点击settings来管理仓库，修改一部分的设置才可以，settings可以点击右上角：

<center>
    <img src="/images/posts/blog/github_new_repo_setting.png" alt="picture not found" style="zoom:100%;" />
    <br>
</center>

进去以后向下拉，将Github Pages下面的Source设置为Master branch即可，至此，博客仓库的创建已经完成了，然后就需要在这个仓库里面填入我们的博客主题和内容控制代码。如果读者喜欢我的博客模板，可以直接从我的github仓库https://chauby.github.io下载，然后使用git checkout命令回到最初的版本即可，最初的版本是一个空仓库，只有简单的示例页面。下载命令为：

```shell
git clone https://github.com/chauby/chauby.github.io.git
```



### 2. 选择自己喜欢的主题

用户也可以自行选择其他主题，在[jekyll主题官网](http://jekyllthemes.org) 上有很多开源的主题，可以选择自己喜欢的，也可以自行搜索jekyll主题，网上有不少开源的主题，选择自己喜欢的即可。



### 3. 基于ruby的本地编写和调试博客内容

克隆到本地的仓库源码不能直接在浏览器中运行，需要通过Ruby环境运行。

[Ruby的下载地址](https://rubyinstaller.org/downloads/)，安装过程的详细教程可参考[Win10安装jekyll和ruby环境](https://mojotv.cn/2019/07/13/install-jekyll-in-windows10)。Ruby下载完成以后直接双击安装，除了安装路径，其他一路默认选项就行。安装路径最好不要包含空格（本人没有完整去验证过，但是我第一次的安装路径包含了空格，后面安装其他东西的时候老是不成功。重新选择了不包含空格的安装路径来安装了ruby后，安装后续的其他问题一路顺利）。

Ruby安装完成以后会弹出一个窗口让你选择3个选项之一来安装，一般直接选3就是，安装过程需要一定的时间。如果这部分没有安装成功，可以使用如下的命令重新安装：

```shell
ridk install
```

这个命令直接在windows的cmd中执行即可，后面的其他安装命令也是一样的。安装成功以后直接回车即可。

上述安装完成以后，需要执行以下命令安装bundle:

```shell
gem install bundle
```

然后是安装jekyll，由于github pages是基于jekyll，所以我们本地安装jekyll以后进行本地的网页调试，最后呈现的结果与在线的是一样的，调试完成了在推送到github仓库部署就行。
```shell
gem install jekyll
```

最后需要安装github-pages，这部分会持续安装很多东西，所以耗时比较长，耐心等待即可。
```shell
gem install github-pages
```

<center>
    <img src="/images/posts/blog/blog-build-blog.png" alt="picture not found" style="zoom:100%;" />
    <br>
</center>
至此，所有的安装工作已完成，此时cd到对应博客的目录，运行以下命令即可：

```
bundle exec jekyll serve
```
上面命令是默认使用4000端口加载网页，网页地址为localhost:4000（或127.0.0.1:4000）。原文中是以下命令：

```
bundle exec jekyll serve -P 5555 --watch
```

`--watch`表示这个本地网页是实时刷新的，当你更改网页的内容时它能实时的变化，而不用不断重启和加载网页。`-P 5555`参数是指定端口号为`5555`，Jekyll默认的端口号是4000，会与福昕阅读器的端口号冲突（如果你的电脑安装了福昕阅读器），所以还是指定端口号最佳（端口设置随自己喜好）。正常情况下你能看到类似下图的启动界面了，此时在浏览器的地址栏输出 `localhost:5555`就能看到你的博客了。如果不行，请参考后文的[常见问题和解决办法](#常见问题)。

![Successful](/images/posts/blog/jekyll-serve-successfully.png)

到这里，博客的平台搭建就算完成了，可以在本地调试完写好的博客然后再使用git推送到github的远程仓库，远程仓库的博客就更新了。

### 4.常见问题

#### 1. 提示 Could not find gem 'tzinfo-data'

![Error 1](/images/posts/blog/jekyll-err1.png)

则打开终端切换到`user.github.io/`路径下，然后运行以下命令：

```shell
bundle install
```

然后等待安装tzinfo、tzinfo-data、wdm等，需要等待一段时间。

#### 2. 提示 Error: Permission denied -bind(2) for 127.0.0.1:4000

![Error 2](/images/posts/blog/jekyll-err2.png)

出现这个问题是提示端口号被占用，因为Jekyll默认的端口号是4000，可能与其他软件冲突（例如福昕阅读器）。所以最好的办法是运行jekyll的启动命令时指定端口号（例如5555）：

```shell
bundle exec jekyll serve -P 5555 --watch
```

注意：此时浏览器要想访问本地的博客内容，应该输入 localhost:5555 。




## 三. 博客的编写

本文所采用的模板编写博客时非常简单，根目录文件路径如下图所示：

<center>
    <img src="/images/posts/blog/my_blog_folder.png" alt="picture not found" style="zoom:100%;" />
    <br>
</center>

其中，_posts目录下分类存放了我的所有博客文章的源文件，博客所使用到的图片都放在images目录下，而平时最主要用到的目录就是这两个，只要在其中添加相应的文件和图片即可完成博客的编写，非常方便。

文章前需要加识别字段，用来分配文章路径页面等。

```markdown
layout: post
title: template page //文章标题
categories: [cate1, cate2]//路径，用[]括起来
description: some word here//描述，暂时好像没发现有什么用
keywords: keyword1, keyword2
```

文章文件命名也需要严格以`yyyy-mm-dd-标题.md`命名，如`2022-07-03-Oracle从删库到跑路.md`

如果我们想要添加、减少或改变博客首页的板式，可以编辑`_config.yml`文件，其中的细节这里不再赘述，大家可以自行摸索。目录pages/下面是博客的各个板块的网页文件，用户也可以自行添加和删除，但是要配合修改`__config.yml`文件。



## 四. 修改信息

网站采用jekyll基于配置文件自动生成，创建网站时需要把config.yml中的信息修改成你自己的。

### _config.yml 

| url             | Github Page地址    |
| --------------- | ------------------ |
| title           | 网页标题（左上角） |
| author          | 作者               |
| github_username | Github用户名       |
| navs            | header中的网页     |
| repository      | 仓库地址           |



## 五. 参考



1. 本博客的搭建过程使用了Zhuang Ma的博客主题[码志](https://mazhuang.org)，此处致谢。


