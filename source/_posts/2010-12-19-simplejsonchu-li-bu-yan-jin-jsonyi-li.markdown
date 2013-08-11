---
layout: post
title: "simplejson处理不严谨JSON一例"
date: 2010-12-19 19:08:22
comments: true
categories: [Python, JSON]
---

一个标准、严谨的JSON应该如下：

    {"title": "\u6587\u7ae0\u6807\u9898\n\u6362\u884c"}

但是在某些情况下，特别是跨语言情况下，JSON可能是这个样子：

    {"title": "文章标题
    换行"}

这种情况下直接使用 simplejson.loads(json) 有可能报如下错误：

    Traceback (most recent call last):
      File "testjson.py", line 24, in <module>
        print simplejson.loads(json)
      File "/System/Library/Frameworks/Python.framework/Versions/2.5/lib/python2.5/
    site-packages/PIL/__init__.py", line 384, in loads
    
      File "build/bdist.macosx-10.5-i386/egg/simplejson/decoder.py", line 402, 
    in decode
      File "build/bdist.macosx-10.5-i386/egg/simplejson/decoder.py", line 418, 
    in raw_decode
    simplejson.decoder.JSONDecodeError: Invalid control character at: line 1 
    column 15 (char 15)
simplejson.loads() 有一个手册上没有提及的参数“strict”，这其实是 JSONDecoder 的一个构造参数，即不严格检查JSON语法。

因此，兼容非标准格式的方法即：

    simplejson.loads(json, strict=False)