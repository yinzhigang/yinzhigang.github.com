---
layout: post
title: "svn: Can't move '.svn/tmp/entries' to '.svn/entries': Operation not permitted"
date: 2010-04-09 10:27:41
comments: true
categories: [Mac OS, SVN]
---

SVN 总是在 Mac OS 下出现这句错误提示，这个问题一般在与 Windows 共用一个目录，并在 Windows 下进行过 svn up 操作后，[老外](http://www.devcha.com/2008/03/mac-os-cant-move-svntmpentries-to.html)对此给出了解决方法，但是最近这个站点在国内经常打不开，在此记一笔为自己备记。

进入项目目录执行：

    chflags -R nouchg .

老外给的方法是：

    chflags -R nouchg *

但是有时会依然会无法解决问题，两种方法都试试吧。
