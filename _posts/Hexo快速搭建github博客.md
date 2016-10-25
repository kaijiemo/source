---
title: Hexo快速搭建github博客
date: 2016-10-23 14:30:15
tags: hexo
categories: 技术文章
---
> 一直想自己在github上面搭建个博客，免费又省事。周末闲来无事，就做了，现在记录一下。
静态博客框架有Hexo和Jekyll等，它们的区别请自行查询，我选[Hexo](https://github.com/hexojs/hexo/) 

# 准备

- github 
- git 
- node.js
- hexo

因为需要在本机上面安装一些必要的软件，我的是Mac os，所以我下载了`Homebrew`，可以理解为它是QQ软件助手这样的东西，需要什么软件都可以在`Homebrew`里面安装，Mac 直接在终端里面运行如下命令即可

<!--More-->

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

官网为：[Homebrew](https://brew.sh)
下面介绍的Mac 的软件安装方法全部都是用终端命令安装的，所以必须先安装`Homebrew`

# 注册github

如果你还没有github账号，请在官网注册 [github官网](https://github.com)
登录后，新建一个和你github账号一样的Respository，***注意名称一定不能是别的，否则你用“yourname.github.io”这样的名称访问不了你的博客的***
至于为什么，详情请看 [github pages 官网介绍](https://help.github.com/articles/user-organization-and-project-pages/)

看如下步骤

![github步骤1.png](http://upload-images.jianshu.io/upload_images/3359560-85dbd750f477232a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![github步骤2.png](http://upload-images.jianshu.io/upload_images/3359560-20f6cc653789f2c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击 绿色的**[Create repository]**成功新建库
暂时github先到这步，最后的步骤还需要回到github的，我们继续往下做

# 安装git

- Mac 

安装git，如果你已经安装了Xcode 套件，那么git已经自带了，如果没有安装Xcode那么在终端里面运行

```
$ brew install git
```

看一下终端的显示信息，就很容易判断是否安装成功了，一般情况下如果网络没有问题，那么肯定都是安装成功的，如发生了错误，那么再运行这个命令就是了。
去官网直接下载安装包也可以 [git官网](https://git-scm.com)

- windows

 直接去官网下载吧 [git官网](https://git-scm.com)

# 安装node.js

- Mac

在终端里面直接运行

```
$ brew install node
```

看终端信息，是否安装成功，成功了继续往下看，不成功再运行一次
或者直接去官网下载安装包[node.js官网](https://nodejs.org/en/)

- windows

直接去官网下载安装包[node.js官网](https://nodejs.org/en/)

# 安装Hexo 

- Mac 和windows 都一样 

在终端运行

```
$ npm install -g hexo-cli
```

安装完后，在终端输入

```
$ hexo
```

如果终端出现如下的信息，那么就是成功安装了

![hexo安装成功.png](http://upload-images.jianshu.io/upload_images/3359560-e827e3d375aa5169.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

到目前为止，所需的软件都安装好了，继续往下看

# 生成博客框架

 Mac 和Windows都一样
 
> 新建一个文件夹blog，在终端里面进入到blog文件夹，`如：cd blog `***注意：*** **以下所有hexo相关的命令全部都需要在终端进入定位到blog目录下运行**

- Hexo 初始化博客

```
// 进入到blog 路径 运行
$ hexo init
```

- 安装博客模版所需依赖

```
$ npm install
```

# 写博客文章

- 新建文章

终端定位到blog文件夹，输入

```
$ hexo new '我的博文1'
```

- 编辑文章内容

在打开博客目录，找到新建的文件 *“我的博文1.md”*，这是markdown格式的文件，建议在下载一个Mou [官网](http://25.io/mou/)

![路径.png](http://upload-images.jianshu.io/upload_images/3359560-48e95cefc35cf6ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

编辑里面的内容，如图

![编写文章.png](http://upload-images.jianshu.io/upload_images/3359560-1b29e4f7f192ff11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 发布，本地预览

```
$ hexo server
```

看到终端输出如下信息，就是服务器启动成功

```
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```

打开浏览器，输入

```
http://localhost:4000
```

看到如下

![运行结果.png](http://upload-images.jianshu.io/upload_images/3359560-d60219eaa9f971dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

到这步，本地博客搭建成功了，还剩最后一步，把本地的博客推送到github上面托管就打工告成了

# 把本地博客推送到github

因为第一步的时候，我们已经新建好github的相关账号和要用到的Respository了，为了本机电脑能把上面步骤搭建的博客推送到github上面去，必须要让github认证你的本机是合法有权限推送的机器（或者你不做这步，但是往后每次把博客推送到github的时候，都需要输入账号和密码，比较麻烦），为了省事，我们这样做

- 在终端运行如下命令，生成ssh的密钥

```
ssh-keygen -t rsa -C "Github的注册邮箱地址"
```

待秘钥生成完毕，会得到两个文件id_rsa和id_rsa.pub，找到这两个文件，(可在终端运行`$ open ~/.ssh  `找到这两个文件)打开id_rsa.pub，Ctrl + a复制里面的所有内容，然后进入https://github.com/settings/keys
 Title 随便填，Key 就把刚刚复制的东西粘贴进去
 
![添加ssh.png](http://upload-images.jianshu.io/upload_images/3359560-73884aac9f7c1ebc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 修改博客相关信息，配置和github相关联

![博客目录.png](http://upload-images.jianshu.io/upload_images/3359560-46b7e88bc3c9b7cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

打开`_config.yml`文件，你会看到里面有很多信息，如下

```
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/
# Site
title: Hexo
subtitle:
description:
author: John Doe
language:
timezone:
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:
# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace:
# Category & Tag
default_category: uncategorized
category_map:
tag_map:
# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type:
````

如果你有耐心，一条一条的看就知道每条配置是干嘛用的了。

1. 修改博客网站相关信息


```
title: Hexo  #你网站的名字
subtitle: #你网站的子名字
description: #你网站的描述
author: John Doe #网站的作者，所有人
language: zh-CN #网站的语言
timezone: Asia/Beijing #网站的时区
```

按照你的需要，修改相应的项，**注意：**每一项的填写，其`:`后面都要保留一个空格，下面也一样
其他的一些配置，比如你自己买了域名的话就修改

```
url: http://yoursite.com
```

就不多说了 

2. 部署和github的联系

```
deploy:
    type: git
    repo: https://github.com/kaijiemo/kaijiemo.github.io.git #修改这里为你自己的
    branch: master #必须是在master
```

到了这一步了，配置文件的东西全部搞完，激动人心的时候又来了

3. 推送到github

```
hexo deploy
```

如果运行`hexo deploy` 命令部署博客到Github的时候会报错`ERROR Deployer not found: git`，可以再在blog目录终端里面运行

```
// 安装部署相关的配置
$ npm install hexo-deployer-git --save
```

访问你的 https://yourname.github.io 就能看到你推送上去的博客页面了

**以后每次新增加了页面都终端依次运行如下两个命令即可**

```
$ hexo generate
$ hexo deploy
```

*如果新加了文章每出来，记得终端运行一下`$ hexo generate`*

现在一个全新的博客就诞生了

# 进阶

- 换博客主题
- 多设备同步写blog

待续。。。。。。。

 [hexo 官方指引文档](https://hexo.io/zh-cn/docs/index.html)

