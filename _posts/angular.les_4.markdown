---
layout: post
title:  Angularjs Lesson 3
date:   2016-01-05
categories: angular
---
#angular指令

先看例子

我们想这样来写一个指令

    <popup-window></popup-window>

然后在运行中,呈现出一个弹窗的概念

结构如下

    <div class="popup-window">
        <h2>弹窗标题</h2>
        <div>
            这是弹窗内容
        </div>
    </div>
    

弹窗作为一个组件,想深度复用,那么我们这样来扩展一下弹窗的使用

    <div ng-controller="DemoController as demo">
            <popup-window title="demo.title" content="demo.content"></popup-window>
    </div>
    
    
那么popup-window,就是我们想要实现的可复用的自定义指令.

首先,用上我们前三节学到的概念,

    angular.module("popupWindow",[])
    .directive('popupWindow',function(){
        
        //这就是指令定义的壳子
    });


##首先,我们理解一下,一个指令,必然有自己的模版..因为我们最终呈现的,肯定是相对复杂的一个结构

    angular.module("popupWindow",[])
    .directive('popupWindow',function(){
        
        return {
            template:'<div class="popup-window">
                              <h2>弹窗标题</h2>
                              <div>
                                  这是弹窗内容
                              </div>
                          </div>'
        }
        //这就是指令定义的壳子
    });

当然,我们可以用templateUrl来指定一个页面片地址

可以看到,指令可以有模版属性.

##再次,考虑我们的呈现,我们要用模版,替换掉,还是插入到结构中去?

restrict
E： 表示该directive仅能以element方式使用，即：<my-dialog></my-dialog>
A： 表示该directive仅能以attribute方式使用，即：<div my-dialog></div>
EA: 表示该directive既能以element方式使用，也能以attribute方式使用


那么我们需要定一个scope出来
    angular.module("popupWindow",[])
    .directive('popupWindow',function(){
        
        return {
            restrict: 'E',
            template:'<div class="popup-window">
                              <h2>弹窗标题</h2>
                              <div>
                                  这是弹窗内容
                              </div>
                          </div>',
            replace:true,
        }
        //这就是指令定义的壳子
    });

https://jsfiddle.net/igaves/c2rayL8f/


###我们把值丢进去

https://jsfiddle.net/igaves/t4e5c0xj/

###link,定义一个内部的事件!
https://jsfiddle.net/igaves/5mbgdLdh/

###重新了解一下scope

在directive中,scope完全是可控制的,上述的我们单独给directive定义了scope,并且定义了变量的来源

那我们尝试一下去掉scope

https://jsfiddle.net/igaves/xymdLseo/

看,scope还在!

原来是,当不定义scope的时候,directive,其实是共享当前指令所属scope的!

https://jsfiddle.net/igaves/xymdLseo/1/


好的!这就是directive的概念!,directive其实,就是提供了一个自定义组件指令的方式!大家可以尝试一下自己定义一下指令级.


#定义一个嵌入式指令.

我们来定义一个鼠标的指令.
比如,我们想定义一个右键菜单

    <div class="active" context-menu>在这里点击邮件</div>
    
    
https://jsfiddle.net/igaves/mogf5cow/2/

这个指令,只有一个实现,就是link

link是做什么?



link

可以简单理解为，当directive被angular 编译后，执行该方法


    
