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

- **字符串内存搜索，硬件访问断点**
	- 搜索时机很重要，时机不对或者编码不对可能搜不到结果，注意,utf-16 = ucs-2
	- 附加上不要运行，直接搜索，因为有的游戏会不断出啊关键线程，改变内存，一进来就断下来，搜索的更稳定。
   - 搜索到的结果不要断点在"全文"(文字脚本集)那里，要断在"乱码与文本隔行混合"的拿出搜索结果里。相当于临时变量，好分析
- **Api断点**
	- lstrlenA 直接用od查找引用，每行都断点，断的地方直接查看eax指向的内容就行了。
   - getExtend32，getGlyOutline(拼的不太对)，可能查不全，只有一行啥的。换api多试试把，单步步进，这个就看经验了，我没找出来只找到一行，提取不完整，也许我太菜😂。
   - 试试其他api，说不准其他api有取巧的地方，能多快好省的完成任务。
- **Cheat Engine找hcode**
   - [hwiki](https://wiki.anime-sharing.com/hgames/index.php?title=AGTH/Tutorial)
   - 很详细，弄半天这篇文章才是精华啊，仔细看，不要因为是英文就不看，绝对找h-code的精华
   - 貌似split_data（就是:右边的）这个的作用是分割文本，分割依据是某个值的不同来分割，相同就分为一组，有点像sql语句里的group by




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
