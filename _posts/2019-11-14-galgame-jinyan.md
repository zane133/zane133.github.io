---
layout: post
title: 日文游戏安装的经验
published: true
---

mdf 里的data文件不要转成iso，直接用ultraiso打开然后复制里面的data文件就行

## AGTH文档
> https://github.com/EnderQIU/agth-cn/blob/master/agth-help-zh-CN.md

## H-Code
> https://vn-hooking.fandom.com/wiki/H-Code

## 文本钩子H-code获取思路
> https://github.com/mireado/ITHVNR/blob/d28a1ae6989f9ebb7a921c3b4b6e97b67e93f21c/vnr/vnrhook/src/engine/engine.cc#L2

## x64dbg
- [条件断点](https://bbs.pediy.com/thread-251385.htm)
- 直接右键设置条件断点，勾选“不输出日志”就是直接断下来，不勾选则是不断，输出日志

## krkrz文档
> http://kirikirikag.sourceforge.net/contents/index.html

> https://hydrozoa.felisworks.com/doc/KAG3Doc/contents/index.html

> http://krkrz.github.io/

官网有例子和文件下载，可以自己制作一个简单的galgame

## ks脚本教程
> http://blog.sina.com.cn/s/blog_a1b9d06101010wn4.html


## 关于字符串搜索

- utf-16 > ucs-2

> [UTF-6百度百科](https://baike.baidu.com/item/UTF-16/9032026?fr=aladdin)


&emsp;&emsp;UTF-16可看成是UCS-2的父集。在没有辅助平面字符（surrogate code points）前，UTF-16与UCS-2所指的是同一的意思。但当引入辅助平面字符后，就称为UTF-16了。现在若有软件声称自己支持UCS-2编码，那其实是暗指它不能支持在UTF-16中超过2bytes的字集。对于小于0x10000的UCS码，UTF-16编码就等于UCS码。

所以，CE和x64dbg日文搜索的时候，可以用utf-16或者Shift-JIS搜索。

## 流程
![image.png](https://i.loli.net/2020/01/08/NQJjDxB3lPncoZe.png)
