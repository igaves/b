---
layout: post
title:  zepto tags
date:   2015-12-06 10:21:30 +0800
categories: developer
---

为了适应移动端的页面开发，需要把对应的移动端特有事件（触摸，两指缩放，左右上下滑动,长按等等），还有移动端动画（css3，requestAnimationFrame)进行更直接的封装。
并且在移动端，很多兼容性问题就可以忽略掉，所以直接用jquery会很大，并且缺失特殊事件，所以，我们选择用zepto

Zepto的设计目的是提供 jQuery 的类似的API 。Zepto设计的目的是有一个5-10k的通用库、下载并快速执行、有一个熟悉通用的API，包含常用的手势事件，css3特效动画控制等功能，所以你能把你主要的精力放到应用开发上。

#初级入门概念知识
   
 - ##基本概念

   - ### 类似jQuery的选择器

     基本上类似于jQuery,ID,name,class,attribute等选择类型可以直接通用

   - ### Dom操作处理

     基础的Dom操作功能，包括处理Dom的样式，className，attribute，dom的插入删除，css处理，等等

   - ### 网络处理

    Ajax处理，包括get，post ，jsonp，等

 - ## 移动设备特性

   - ### touch events

    tab,singleTap,doubleTap,longTap,swipe(left,right,up,down)等

   - ### Detect module 

    移动设备也有兼容性 
    设备检测，针对不同设备处理不同兼容性

   - ### fx

    基于css3的动画特效库，开启GPU 加速后，让动画在移动设备上更流畅，translate(X|Y|Z|3d) rotate(X|Y|Z|3d) scale(X|Y|Z) matrix(3d) perspective skew(X|Y) 等


   - ##实战

     做一个上滑翻页的微信页面,并且利用*animate.css* 在页面上加入动画效果
