---
title: 基于Hexo的博客系统
date: 2017-12-21 10:21:20
description: hexo的安装配置 、使用hexo、github pages搭建博客以及部署博客等详细信息
tags:
    - hexo
---

> 作为一个猿儿，怎么能少了写博客呢，也一直在写着，中间也折腾了各种方法，但最终还是决定换成了简单易上手的Hexo+github pages+Mweb了，把重点放在内容上才是正确的选择,既然这样，那本文就先简单介绍一下  [hexo](https://hexo.io) 以及使用hexo 、github、 [Mweb](http://zh.mweb.im)(基于markdown的写作工具)  搭建博客和部署等详细信息。


# 官方文档
欢迎来到 [hexo](https://hexo.io) !    如本文不能满足您的需求，你也可查看官方 [中文文档](https://hexo.io/zh-cn/docs/index.html)  如遇到一些问题 可查看 [问题解答](https://hexo.io/zh-cn/docs/troubleshooting.html)
# 什么是Hexo

> Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

# 安装

## Hexo安装前提
安装 Hexo 相当简单。然而在安装前，您必须检查电脑中是否已安装下列应用程序：

*  [Node.js](https://nodejs.org/)
*  [Git](https://git-scm.com/)

可通过终端命令确认上述环境是否安装：

``` 
$ node -v
$ git --version
```
安装后命令显示结果如下：
{% asset_img 15138271006708.jpg %}

如果您的电脑中已经安装上述必备程序，那么恭喜！接下来只需要使用 npm 即可完成 Hexo 的安装。

```
$ npm install -g hexo-cli
```
如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

## 安装Git

> Mac 用户
> 在编译时可能会遇到问题，请先到 App Store 安装 Xcode，Xcode 完成后，启动并进入 Preferences -> Download -> Command Line Tools -> Install 安装命令行工具。


* **Windows:**下载并安装 [Git下载](https://git-scm.com/download/win)。 **另**: 有个叫做 msysGit 的项目也提供了安装包 [Git下载2](http://msysgit.github.com/) 这种方式完成安装之后，就可以使用命令行的 git 工具（而且已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。
* **Mac：**在Mac上安装Git有3中方式，如下：
    1. **推荐** 使用 [homebrew](https://github.com/mxcl/homebrew)：`$ brew install git.`
    2. 通过 [MacPorts] (http://www.macports.org) 安装。如果已经装好了 MacPorts，用下面的命令安装 Git：

     ```
     $ sudo port install git-core +svn +doc +bash_completion +gitweb
     ```
    这种方式就不需要再自己安装依赖库了，Macports 会帮你搞定这些麻烦事。一般上面列出的安装选项已经够用，要是你想用 Git 连接 Subversion 的代码仓库，还可以加上 +svn 选项
    3. 图形化的 Git 安装工具 [下载](http://sourceforge.net/projects/git-osx-installer/)
* **Linux** (Ubuntu, Debian):   `$ sudo apt-get install git-core` 或 `$ apt-get install git`
*  **Linux** (Fedora, Red Hat, CentOS):  `$ sudo yum install git-core`  

## 安装Node.js

* 下载 [安装程序] (https://nodejs.org/en/download/) 来安装。
* hexo官方推荐安装 Node.js 的方式是使用 [nvm](https://github.com/creationix/nvm)。

cURL:

```
$ curl https://raw.github.com/creationix/nvm/master/install.sh | sh
```
或者 Wget:

```
$ wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
```
安装完成后，重启终端并执行下列命令即可安装 Node.js。

```
$ nvm install stable
```
> Windows 用户
> 对于windows用户来说，建议使用安装程序进行安装。安装时，请勾选Add to PATH选项。
> 另外，您也可以使用Git Bash，这是git for windows自带的一组程序，提供了Linux风格的shell，在该环境下，您可以直接用上面提到的命令来安装Node.js。打开它的方法很简单，在任意位置单击右键，选择“Git Bash Here”即可。由于Hexo的很多操作都涉及到命令行，您可以考虑始终使用Git Bash来进行操作。

## 安装Hexo

所有必备的应用程序安装完成后，即可使用 npm 安装 Hexo。

```
$ npm install -g hexo-cli
```
# 建站

hexo安装完成后，接下来就是建站了，建站其实也很简单，首先进入一个目录(作为存放博客资源的目录),然后执行如下命令：

```
$ hexo init  blog
$ cd blog
$ npm install
$ hexo server
```
> blog 为文件夹名称,   
> hexo server 是启动本地博客服务命令

正常情况下，终端中将会输出如下的结果

```
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
这样的话博客算是初步建成了，打开浏览器，输入地址：`http://localhost:4000/ `就可以访问了，将会显示如下界面
{% asset_img 15139224941949.jpg %}

# 配置

## 目录说明
网站初步建成后，接下来就可以进行相应的配置了,我们可以先看一下目录信息：

```
_config.yml		
source		
package.json		
themes
node_modules		
scaffolds
```
**_config.yml** : 网站的 配置 信息，您可以在此配置大部分的参数
**package.json**:  应用程序的信息。EJS, Stylus 和 Markdown renderer 已默认安装，您可以自由移除。
**scaffolds** :  [模版] (https://hexo.io/zh-cn/docs/writing.html)文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。
> Hexo的模板是指在新建的markdown文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改。

**source** :Hexo的模板是指在新建的markdown文件中默认填充的内容。例如，如果您修改scaffold/post.md中的Front-matter内容，那么每次新建一篇文章时都会包含这个修改。
**themes**:  [主题](https://hexo.io/zh-cn/docs/themes.html) 文件夹。Hexo 会根据主题来生成静态页面

## 网站配置

网站的主要配置都在根目录 `_config.yml ` 文件里面:

**网站**

```
# Site
title: Hexo
subtitle:
description:
author: John Doe
language:
timezone:
```

| 参数          | 描述                                       |
| ----------- | ---------------------------------------- |
| title       | 网站标题                                     |
| subtitle    | 网站副标题                                    |
| description | 网站描述                                     |
| author      | 您的名字                                     |
| language    | 网站使用的语言 可以选配 en 或者 zh-cn                 |
| timezone    | 网站时区。Hexo 默认使用您电脑的时区。[时区列表](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)。比如说：Asia/Shanghai |

其中，description主要用于SEO，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。author参数用于主题显示文章的作者。

**网址**
这个部分需要修改的只有 url 选项，改成博客地址行了。后面的链接生成规则，保持不变即可。

```
# URL
url: http://yoursite.com     #网址
root: /                                  #网站根目录
permalink: :year/:month/:day/:title/       #文章的永久链接格式
permalink_defaults:   #永久链接中各部分的默认值
```

>  网站存放在子目录
>  如果您的网站存放在子目录中，例如 http://yoursite.com/blog， 则请将您的 url 设为 http://yoursite.com/blog 并把 root 设为 /blog/。


```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape
```
这一组配置是用来定义主题和配置插件的，可以看到，官方默认的主题叫做 ` landscape`  ,更多主题 可以查看[官方列表 ](https://hexo.io/themes/)

例如选择yelee
```
git clone https://github.com/MOxFIVE/hexo-theme-yelee.git themes/yelee
```
把从官方列表中查到的主题仓库地址 `git clone` 下来，放到 `themes/ `下相应的目录中，然后我们修改博客根目录下的 `_config.yml `文件

```
theme: yelee
```
## 文章资源文件管理

> 对于那些想要更有规律地提供图片和其他资源以及想要将他们的资源分布在各个文章上的人来说，Hexo也提供了更组织化的方式来管理资源。这个稍微有些复杂但是管理资源非常方便的功能可以通过将 `config.yml`文件中的 `post_asset_folder` 选项设为 `true` 来打开

1.首先确认`_config.yml` 中有 `post_asset_folder:true`。

```
_config.yml
post_asset_folder: true
```

2.创建博客是使用命令创建：

```
hexo new test
```

> 使用完命令之后，在source/_post文件夹里面就会出现一个“test.md”的文件和一个“test”的文件夹。

下一步就是把需要的图片放到新创建的那个**文件夹**里面去。

引用方法如下：

```
{% asset_img example.jpg This is an example image %}
```

更多信息，请查阅 Hexo 的 [官方文档](https://hexo.io/zh-cn/docs/index.html)。

# 写作

撰写博文也非常简单，在你的博客目录 blog 下键入命令：

```
$ hexo new [layout] <title>
```
您可以在命令中指定文章的布局（layout），默认为 post，可以通过修改 _config.yml 中的 default_layout 参数来指定默认布局。Hexo 有三种默认布局：post、page 和 draft，它们分别对应不同的路径，而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。

例如：

```
hexo new post <title>
```
就可以新建一篇博文了，如果你想写一篇草稿，而不发布的话，那么你可以键入：

```
hexo new draft <title>
```

更多信息，请查看 [官方文档](https://hexo.io/zh-cn/docs/writing.html)

# 博客部署

我们用来托管博客的服务叫做  [Github Pages](https://pages.github.com/)，它是 Github 用来提供给个人/组织或者项目的网页服务，只需要部署到你的 Github Repository，推送代码，便可以实时呈现。

首先，你需要有一个 Github 的账号。然后创建一个名称为 `<username>.github.io `的仓库来托管网页即可。

以我的 Github 为例，我的用户名是 xiejianbing，所以创建一个名为 xiejianbing.github.io 的仓库，创建的仓库地址便是：https://github.com/xiejianbing/xiejianbing.github.io.git 创建完后，我们可以暂时不用管它，不需要往仓库里面 push 任何的东西。

**Hexo 部署配置**
在博客的根目录下有一个名为` _config.yml `的文件，这是博客的主配置文件。前面的其他部分我们先不理会，后文再谈，我们先看最后的 `Deployment `配置项：

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type:
```
根据官方的文档显示，现在 Hexo 支持 Git、Heroku、Rsync、OpenShift、FTPSync 等部署方式，我们选择 Git 来部署的话，需要首先安装 hexo-deployer-git 插件：

```
 npm install hexo-deployer-git --save
```
然后编辑上面的配置文件

```
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
```
我们需要把刚才创建的仓库地址添加进来，branch 和 message 项可以不填，默认情况下推送到 master 分支，这里我建议使用 SSH 加密的仓库地址（参看 [Github 官方文档配置](https://help.github.com/articles/generating-an-ssh-key/) SSH 免密操作）

保存配置文件之后，我们在博客的根目录键入：

```
hexo generate
hexo deploy
```

上述命令可以简化成

```
hexo g -d
```
便可以把博客部署到 Github 了。现在，所有人都可以通过 `http://<username>.github.io` 来访问自己的博客。

# 博客域名绑定

>我在阿里云上够买了一个域名 `xiejianbing.com`  现在绑定到我的博客地址xiejianbing.github.io上

* 第一步 添加CNAME文件

  在个人博客仓库的根目录中新建文件`CNAME`（注意没有后缀），该文件内容就是需要绑定的域名地址(自己购买的域名地址)`xiejianbing.com`，告诉Github Pages服务器你想指定的域名。该域名不能包含前缀信息，即不能添加`http:\\`前缀。


  注： 在写文章时 CNAME文件放在hexo的source文件夹下  否则在执行`hexo g -d` 命令时会被删除

* 第二步 绑定域名

  登录[阿里云控制台](https://netcn.console.aliyun.com/core/domain/list) 进行域名解析  如下图：

  {% asset_img yumingjiexi.jpg %}

  记录值，也就是ip地址 可以通过`ping  xiejianbing.github.io`获取