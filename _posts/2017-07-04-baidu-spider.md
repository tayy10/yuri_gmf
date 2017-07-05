---
layout: post
title: Github Pages如何被百度收录
categories: GithubPages
tag: [github pages, spider, 百度蜘蛛]
excerpt_separator: <!--more-->
description: Github Pages如何被百度收录
keywords: githubPages,蜘蛛,百度,coding,cname
---
# Github Pages 不被百度蜘蛛抓取的问题
由于之前的利用百度统计导致的针对`Github`的`DDos`攻击事件，`Github`屏蔽了百度蜘蛛对于`Github Pages`的爬取收录，这对国内使用`Github Pages`的用户无疑是一个巨大的打击。
我也不例外，这两天用尽了各种办法，`Google`大法还是不错的，昨天下午提交的`sitemap`，今天上午就都收录了。针对百度，也搜索了很多办法，主要有以下几种：
## 1. 利用`CDN`
经论证，并没有什么卵用
<!--more-->
## 2. 利用镜像，针对百度蜘蛛，解析到镜像服务器上
- 1.　有自己的服务器或者`VPS`的略过，别问为什么，因为我没有，哈哈哈。
    PS：其实大致过程大差不差。
- 2.　由于我这个屌丝没钱买服务器，所以只能利用`coding.net`进行托管，在百度蜘蛛爬取的时候，解析到`coding pages`
- 有人说使用`Git cafe`，偷偷告诉你，`git cafe`已经被`coding`给买了，所以，老老实实用`coding`吧
- 下面开始放大招
> ### 首先第一步，需要在`Github`上新建一个项目，这个问题应该不大吧，既然都用`Github Pages`了，这一步就不重复赘述了。
>
> ### 其次第二步，在`coding.net`中从`Github`导入项目
> ![导入项目](https://ooo.0o0.ooo/2017/07/05/595ce5dcb28a9.png)
> ### 第三步，开启`coding`的`pages`服务，`coding`的`pages`服务跟`Github`的`pages`服务的区别在于：`coding`使用的分支是`master`或`coding-pages`,`Github`使用的分支是`master`跟`gh-pages`,为了统一，建议使用`master`分支。
>![设置`pages`分支及自定义域名](https://ooo.0o0.ooo/2017/07/05/595ce60dd86a9.png)
> PS:`coding`的坑：
> 1. 分支跟`github`不一样
> 2. 自定义域名需要银牌会员以上才能开启，银牌会员需要完善自己的账号资料即可开启（注意：不管是不是必填都要填才可以开启银牌会员）
> 3. 使用`coding`的自定义域名，有一个问题，金牌及以上会员可以略过，如果是银牌会员，`coding`会先定向到一个`coding`提供的页面，之后才会重定向到你的自定义域名，除非。。。
> 除非你在底部加上`Hosted by coding pages`
>
> ### 第四步，针对`git`的`push`添加多个源
```javascript
git remote set-url --add --push origin ****
```
> 将`****`分别换成你自己对应的`Github`以及`coding`的项目地址
> 之后，使用`git push origin master`就可以将本地更改同步提交至`Github`跟`coding`
>
> 至此，镜像网站部分应该都已经搞定了，如有遗漏，自己研究研究吧。嗯哼~

> ### 第五步，通过`DNSPod`对域名进行解析
> 添加`CNAME`解析，针对百度解析值`pages.coding.me`，其余的解析到`github.io`。
> 可能有人要问，为啥不直接用`coding pages`呢？鉴于服务稳定性以及`Github`挺给力的`cdn`加速，暂时没有这方面的打算。
> ![添加域名解析](https://ooo.0o0.ooo/2017/07/05/595ce63668cb8.png)
> 之所以采用这个方案，也是对比了一下，觉得这个比较靠谱，说说我的比较过程吧
> 1. 利用阿里云进行域名解析，不过针对百度的解析，好像支持的并不好，所以放弃了
> 2. 七牛云等`cdn`加速，由于域名未备案，所以直接就`pass`了
> 3. 百度云免费`cdn`加速，效果也不太好，缓存设置略微有点坑爹，放弃，不挣扎了。

<br/><br/>
不知道有没有人懂这种心情，都快哭了。好了，就这样吧，观察几天看看有没有问题，没问题的话，此贴就可以终结了，如果还有问题，那估计过几天你们就看不到这张帖子了。笑哭。。。。🤣
![百度抓取](https://ooo.0o0.ooo/2017/07/05/595ce6610f1b7.png)