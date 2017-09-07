---
layout:     post
title:      解决软键盘遮挡input或textarea问题
subtitle:   
date:       2017-09-07
author:     ZY
header-img: img/post-bg-2015.jpg
catalog: true
tags:
    - webApp
    - javaScript
---



## 前言

在开发 Android 手机表单经常遇到软键盘弹出后遮挡 input 和 textarea 表单的情况,而 ios 文本被 focus 之后都会自动移动到合适位置。当 Android 手机的软键盘弹出后会导致页面被压缩，因此我们可以监听 window 的 resize 事件来判断软键盘的弹出和关闭。然后在利用 scrollTop 将输入框滚动定位到Html的合适位置即可。

<p id = "build"></p>
---

## 正文

具体思路如下：
1. 监听软键盘弹出事件
2. 设置html高度为150% ，这样做的目的是为了让html高度小于屏幕时，依然能够显示滚动条。
3. 将滚动条滚动到合适位置

具体实现代码如下：


```
//Android监听软键盘操作
var winHeight = $(window).height(); //获取当前页面高度
    $(window).resize(function() {
        var thisHeight = $(this).height();
        if (winHeight - thisHeight > 50) {
            //当软键盘弹出，在这里面操作
            $("html").css("height", "150%");
            $("html").scrollTop(200)
        } else {
            //当软键盘收起，在此处操作
            $("html").css("height", "100%");
        }
    });
```

另外需要注意在ios手机上，软键盘弹出是监听不到resize事件的，但是由于ios的表单会根据软件盘弹出自动移动到合适位置，这里也就没再继续深入研究。




---




