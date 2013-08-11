---
layout: post
title: "开始使用vim作主要开发工具"
date: 2012-12-28 22:34
comments: true
categories: vim
---

经过这么多年，IDE与编辑器用了不少，从开始的EditPlus到ZendStudio再到Eclipse、NetBeans、TextMate、Sublime Text等等。

几年前也曾经尝试过VIM、Emacs，但当时一是年少无知，二是插件没有如今这么丰富与强大，特别是在VIM支持Python、Ruby等脚本语言开发插件后，插件功能日益强大，甚至可以达到IDE标准，还有UltiSnips实现了类似TextMate的tab功能。加上灵活的自定义功能，让经过几年漂泊的我发现这几十年前诞生的编辑器竟如此强大。所以就这样了，选定离手。

下面是一些目前我使用的插件：

 * vundle (最好用的VIM插件管理工具，当年插件安装复杂也是我无法继续的原因之一)
 * UltiSnips (仿TextMate的TAB补全，支持Python写snips)
 * NERDTree (项目目录树)
 * NERTCommenter (代码注释，支持多种语言)
 * TagBar (显示类方法、函数列表、属性等导航)
 * neocomplcache (代码提示)
 * vim-octopress (本博客代码加亮)
 * phpcomplete.vim (PHP代码自动完成)
 * javacomplete (JAVA代码自动完成)
 * zencoding.vim (HTML快速书写)
 * numbers.vim (在命令模式显示与当前行间隔的行数，用于快速定位)
 * powerline (漂亮的状态栏)
 * matchit (快速找到标签的开始或结束位置)
 * AutoClose (自动关闭括号、引号)

我的.vimrc配置已经发布到GitHub: https://github.com/yinzhigang/dotvim
