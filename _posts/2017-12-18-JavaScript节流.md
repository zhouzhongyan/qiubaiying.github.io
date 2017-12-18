---
layout:     post
title:      JavaScript节流
subtitle:   
date:       2017-12-18
author:     Zhouzhongyan
header-img: img/post-bg-coffee.jpeg
catalog: true
tags:
    - javaScript
---
# 场景
在监听页面滚动（scroll），div大小变化（resize）以及其他防止事件的多次触发的情景下，我们可以使用“节流”来处理。

# 原理
在监听事件中，使用 setTimeout(code,millisec) 方法，包裹要执行的方法。如果在设定的 millisec 时间内，重复执行了话，就使用clearTimeout(id_of_setTimeout) 将 setTimeout 的方法清理掉，直至监听到最后一次事件的触发，执行最终的 setTimeout 方法。
# demo
```
let tt;

function callback(){
  //事件触发执行的具体操作
  ...
}

window.addEventListener("scroll",function(){
        clearTimeout(tt);
        tt = setTimeout(callback,50)
},false);

```
