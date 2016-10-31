---
title: 域名绑定到hexo github个人网站
date: 2016-10-27 22:52:25
tags: hexo
categories: 技术文章
---
> 一个有B格的个人网站怎么能少个有个性的域名呢

# 购买域名

域名这种东西去阿里万网注册一个就是了，这里强调一下如果注册的是`.cn`这种国内的域名是需要备案的也就是特么的要实名制的。所以建议大家不折腾就注册一个国际域名

买域名就像淘宝购物一样，在万网上面先查找自己喜欢的域名，然后加入购物车，支付宝付费，结账，域名是你的了

<!--More-->

# 绑定域名

按如下截图步骤一步一步绑定

![1.管理控制台－dns云解析.png](http://ofpj3npwe.bkt.clouddn.com/1.%E7%AE%A1%E7%90%86%E6%8E%A7%E5%88%B6%E5%8F%B0%EF%BC%8Ddns%E4%BA%91%E8%A7%A3%E6%9E%90.png)

![2.添加解析.png](http://ofpj3npwe.bkt.clouddn.com/2.%E6%B7%BB%E5%8A%A0%E8%A7%A3%E6%9E%90.png)

![3.管理域名.png](http://ofpj3npwe.bkt.clouddn.com/3.%E7%AE%A1%E7%90%86%E5%9F%9F%E5%90%8D.png)

![4.修改域名解析dns.png](http://ofpj3npwe.bkt.clouddn.com/4.%E4%BF%AE%E6%94%B9%E5%9F%9F%E5%90%8D%E8%A7%A3%E6%9E%90dns.png)

其中第四步那个dns不能用默认的，一定要改成我上图的那个地址

```
f1g1ns1.dnspod.net   
f1g2ns1.dnspod.net
```

然后耐心的等上48小时，等你的域名解析扩散到全球

# 域名信息推送到github

在你的个人网站根目录 source目录下新建一个`CNAME`文件，不要任何的后缀名，在改文件添上一行`youdomain.com 也即是你的域名`，然后在终端运行

```
$ hexo g
$ hexo deploy
```

现在一切ok，试试你的域名吧（哦，你的域名dns解析可能还没扩散哦，那就再等等，过一段时间再试）