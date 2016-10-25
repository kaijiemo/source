---
title: Hexo进阶
date: 2016-10-24 22:46:32
tags: hexo
categories: 技术文章
---
> 搭建了基本的框架，也写了文章 hexo 还有一些进阶的功能也可以玩玩

# 菜单栏改成中文

打开博客根目录，进入主题文件夹的`languages`文件夹，例如hexo的默认主题就是`landscape`。看到的是这样
<!--More-->

![语言文件夹.png](http://upload-images.jianshu.io/upload_images/3359560-f04c3718aa3c5bc5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

看到没，很明显，那个叫zh-CN.yml的就是对应的英文翻译成中文的名字了，打开

```
categories: 分类
search: 搜索
tags: 标签
tagcloud: 标签云
tweets: 推文
prev: 上一页
next: 下一页
comment: 留言
archive_a: 归档
archive_b: 归档：%s
page: 第 %d 页
recent_posts: 最新文章
newer: Newer
older: Older
share: Share
powered_by: Powered by
rss_feed: RSS Feed
category: Category
tag: Tag

```

新加了菜单栏，只需要把在这里出现对应的中文名即可，如

```
Home: 主页
About: 关于
```


# 开启RSS功能

默认搭建好的网站，点击 *`Rss feed`* (默认在再右上角)，如下图

![Rss feed.png](http://upload-images.jianshu.io/upload_images/3359560-cab6be7fac45fb41.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

是会报错的，在网站根目录，终端运行

```
$ npm install hexo-generator-feed --save
```
即可解决

# 文章里面的图片保存在何处

- 保存在本网站 github上面
打开根目录，找到`source`文件夹，在`source`下面新建一个文件夹叫'images'，然后把你需要在文章里面出现的图片放到这个`images`里面，比如你图片名称为 `niceview.jpg`那么你在文章里面这样写

```
! [本地图片] (/images/niceview.jpg)  
```

这样有个缺点，就是你用`Mou`这样的`Markdown` 编辑器写文章的时候，看不到图片的预览效果，但是，`$ hexo server` 运行起来后，在本地的`http://localhost:4000/` 是可以看到效果的，运行`$ hexo deploy`  推送到github上面，ok，搞掂。

- 使用第三方云存储保存

说到底就是为了找一个地方把图片传上去，然后获取该图片的url
第三方图床也有几个，比如新浪，七牛等，再简单一点，你直接把图片发到你的微博，然后查看这图片的URL也行，我就不折腾第三方了，图片很多的话，可以考虑，否则用上面那种存在本地的方法已经够用了

# 换主题

去官网 [hexo 主题](https://hexo.io/themes/) 挑一个你喜欢的，把它下载回来放到 `themes` 目录里面，然后在网站的根目录找到`_config.yml` 打开找到下面这条配置

```
theme: next #这个 next就是你下载回来的主题

```

把网站运行起来就可以看到主题已换
我用的是这个[next主题](http://theme-next.iissnan.com/getting-started.html)，要更加高级定制的，请点进去看

# 添加评论
我用的是多说，还是直接看官网介绍吧，比较简单
http://theme-next.iissnan.com/third-party-services.html#share-duoshuo

# Read more
如果文章太长，希望只是在首页显示部分，然后出现`Read more>>`按钮，只需要在文章的适当位置写入
```
<!--More-->
```