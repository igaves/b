---
layout: post
title:  Angularjs Tags
date:   2015-11-28 22:21:30 +0800
categories: developer
---

angular 核心是双向绑定，界面的操作，可以触发数据变化，数据的变化，也可以触发界面的变化

这种设计模型，在前端开发中，很多的传统的，接收数据，触发 dom操作，dom操作后，触发接收数据的行为，都可以自动化完成，
开发同学只需要做的一件事，就是在html上嵌入指令，标记出DOM和DOM，DOM 和 DATA之间的关系

比如，ajax请求到了 data:{name:'xiaoming',age:12} ，DOM上标记上了 

    <div>
    <label ng-bind="data.name"></label>
    <input ng-model="data.age" type="text">
    </div>

这不是和模版一样吗？
不，当你data上修改掉后，比如

    data.age+

那么界面就会自动变为13

同理，如果我在input上修改了年纪的输入框

我再
    alert(data.age)
就会发现，data的数据也被修改掉了

angular的核心，就是双向绑定。

#初级入门概念知识
   
 - ##基本概念

   - ###$scope是什么

     scope就是一个数据束的有效空间,其中可以有数据，有方法等等，双向绑定依赖于Scope

   - ###controller & service 是什么

     service是一个单例的对象，只初始化一次
     controller可以理解成控制层，连接数据和界面显示的部分

   - ###module 是什么，angular中的Dependency Inject

     依赖注入是angular的核心内容，所有的注入源都是以模块注入，属于逻辑拆分的一个单元

 - ##指令入门

   - ###ng-repeat 来循环呈现一组数据

     比较类似于for循环，但是这个更有效的是在展示后 ，还会对数据进行监听，数据的变化，会出发自动修正呈现结果，比如给数据push一条数据，删除一条数据，那么ng-repeat 元素会自动呈现 ,是DATA->流的过程

   - ###ng-bind ng-model 等指令实现一组双向绑定
     数据绑定一部分，界面的修改，会引起数据的变化，是DOM->DATA流的过程

   - ###filter 来进行过滤数据
     
     可以看作一个回调，对数据进行筛选等等，可以加入ng-repeat指令内共同作用
  
   - ###ng-show ng-hide 来进行显示隐藏页面元素
     
     对某些数据进行监听，当true& false的时候，自动触发界面的显示隐藏

   - ###ng-style 来进行样式控制

     自动修正dom样式

 - ##指令进阶

   - ###事件绑定，ng-click , ng-mouseevent..

     事件的监听处理

   - ###ng-if ng-else等

     页面的逻辑判断指令

 - ##$http 网络

   - ###get ,post ,delete

   - ###自定义service 

   - ###$resource 简介

     自动化Restful API的model封装

 - ##高阶 自定义指令

   - ###指令中作用域scope

   - ###指令中 $complile

   - ###指令中 controller link

   - ###指令 restrict

 - ##高阶 
   - ###$watch $apply $digest 
   - ###十分钟开发一个TODO LIST
   - ###半小时，开发一个QQ聊天窗口
   - ###管理后台CURD 快速搭建
   - ###测试开发
