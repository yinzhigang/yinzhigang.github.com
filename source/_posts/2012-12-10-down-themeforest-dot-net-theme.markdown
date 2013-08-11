---
layout: post
title: "下载themeforest.net的主题"
date: 2012-12-10 18:35
comments: true
categories: [wget, theme]
---

themeforest.net有很多漂亮的主题，但都是收费的而且还不便宜。但幸好很多主题都提供预览功能，这时我们就可以使用wget神器将HTML、CSS、JS、图片等下载下来，当然Wordpress之类的主题就需要自己写程序来实现功能了。

比如[这个](http://themeforest.net/item/ninja-admin-/21190)简洁的后台管理模板，我们点 Live Prefiew 找到真正的预览地址：http://benblogged.com/dev/ninja\_admin/

    wget -mk http://benblogged.com/dev/ninja_admin/

稍等一会儿，包括CSS图片在内的文件就会被下载到benblogged.com/dev/ninja\_admin/，这个页面比较简单，只有一个HTML，其他复杂些也一样。

如果对方服务器有限制，如限制抓取速度，那么：

    wget -mk -w 20 http://benblogged.com/dev/ninja_admin/

-w 20 代表每隔20秒下载一个文件。

还有服务器限制User-Agent，这也好办：

    wget -mk -U 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_8_2) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.95 Safari/537.11' http://benblogged.com/dev/ninja_admin/

这就模拟成了普通浏览器，怎么样，酷吧。
