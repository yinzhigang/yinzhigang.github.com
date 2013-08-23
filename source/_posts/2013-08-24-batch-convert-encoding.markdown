---
layout: post
title: "批量转换文件编码"
date: 2013-08-24 00:18
comments: true
categories: 
---

适用于Linux及 Mac OS 系统，Windows就抱歉了，你们自己想办法吧。

    find . -name *.java -exec sh -c "iconv -f GBK -t UTF8 {} > /tmp/iconv.tmp" \; -exec mv /tmp/iconv.tmp '{}' \;

以上命令将所有 .java 文件由GBK编码转换为UTF8编码。

注意，网上有很多文章将 iconv 命令写成这样：

    find . -name *.java -exec sh -c "iconv -f GBK -t UTF8 {} > {}" \;

再说一句，上面这种写法是错误的，以上写法相当于 iconv 输出到源文件，但不知是BUG还是别的原因，你只能得到0字节的空文件，所以必须使用第一条命令，先生成到一个临时文件，然后再移动回来。
