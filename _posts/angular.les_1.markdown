---
layout: post
title:  Angularjs Lesson 1
date:   2016-01-01
categories: angular
---
#初步了解AngularJS

OK,到现在阶段,大家应该对JQuery有了一个比较深入的了解
但是从开发层面,jQuery应该属于一个比较基础的前端框架,jQuery本身,对很多浏览器的功能进行了封装,譬如选择器,Dom操作,Ajax操作等等
那么在实际开发中,我们面临的,是很多业务上的功能,jQuery并没有对业务进行抽象剥离,比如数据列表,数据排序,RESTFUL API,等等

那么我们可以总结一下,同学们已经学了一个jQuery,"类库",那么接下来会接触一个完全的"框架"

##Angular,是更高一层的业务抽象,是为了增强现有HTML在构建应用上的不足而开发的

据一个例子,
使用jQuery,控制一个DOM结构的隐藏和显示,我们可以

    $(selector).hide();
    $(selector).show();
    $(selector).toggle();

但是何时进行隐藏,何时进行显示,那么这个业务条件,必须我们在js文件中,来进行代码书写

    if(need_to_show){
        $(selector).show();
    }else{
        $(selector).hide();
    }
    
    //or
    
    if(need_to_show){
        $(selector).removeClass("hidden");
    }else{
        $(selector).addClass('hidden');
    }


在上述的代码中,*need_to_show*其实就是业务判断点

但是在angular中,对此类的业务已然进行了抽象剥离.

    <div class="pop-window" ng-show="need_to_show">
        ....
    </div>
    
控制此DOM显示隐藏,只需要简单的 need_to_show = true 或者 need_to_show = false;

Angular把嵌入dom内的自定义Attribute,叫做*指令*

##我们可以这样来形容,angular本身,就是围绕指令来建立的一套业务增强性框架

一个开发者,完全可以通过简单的写指令,来替代复杂的前端DOM操作代码


OK

这次我们先看一个指令,然后我们再对比传统的jQuery代码.


    <li ng-repeat="item in list" id="item_{{item.id}}" ng-show="item.available">
        {{item.content}}
    </li>

https://jsfiddle.net/igaves/fdurqxf2/2/

我们再看原生的应用

    function createList(list){
        var html = '';
        for(var i=0;i<list.length;i++){
            var item = list[i];
            var style = '';
            if(!item.available){
                style = 'style="display:none"';
            }
            html+='<li id="item_'+item.id+'" '+style+'>'+item.content+'</li>';      
        }
        
        $("#list").html(html);
    }
    
https://jsfiddle.net/igaves/va9j4jkL/

当然,你也可以用流行的前端模版引擎来实现,譬如artemplate,Mustache

两者的呈现效果是一样的,

那么为什么用Angular呢?

我们来看,如果我们要给这个list,新添加一项数据

那么原声的应用,看起来需要重新执行一遍createList这个函数才行..

那么,删除,更新,不管任何操作,看起来都要重新执行

但是,Angular没有这个操作.

Angular,仅仅需要修改list这个数据

界面内容自动更新掉了!

 1.angular仅仅操作了数据
 1.angular不需要多余的绑定事件,只需要在UI上写逻辑即可
 1.angular不需要额外的操作DOM的方法
 1.angular把UI层面的东西放在了代码之外,界面的变化,直接修改界面元素即可

简单的列表行为,可以
这简直是魔法.

#这就是angular的核心亮点,数据双向绑定

数据变化,可以直接触发UI的变化.

好的,大家应该对于angular有了个初步的了解

那么我们来看angular的构成

>我们先要了解一下angular项目的基础概念,app,module,controller等,app是程序入口,module是对于功能模块性的拆分定义,controller就是对于界面的控制部分
>围绕界面,我们要统一看一下都有那些有意思的指令,比如ng-model,ng-hide,ng-mousedown ng-repeat
>非界面部分,angular提供了service(provider factory)概念,就是非界面的功能性元素包装模块,供controller来调用

我们掌握了上述几个点,那么80%的项目,基本上可以快速的推进开发了!

进阶部分,我们来深入了解一下指令,创建自己的指令

>自定义指令,angular的扩展方式!



