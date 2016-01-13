---
layout: post
title:  Angularjs Lesson 3
date:   2016-01-05
categories: angular
---
#angular指令集合

##dom操作指令

ng-show&ng-hide

ng-if

ng-class

ng-bind

ng-include 


{{}}

##数据绑定指令

ng-model

ng-select

ng-bind


##事件指令 

ng-click

ng-mouseenter/move/up/down

ng-{{event}}


>上述都是基础指令,可以直接演示给学院看

##scope的概念
#scope 是在应用 controller 与 view 之间的纽带

_这里是超级重点,一定要让同学理解是怎么回事_

scope,类似于this念,作用域,上下文的概念,在页面指令中绑定的数据,都会指向于一个scope. 比如 ng-bind="name",那么这个name,一定是controller中的,scope.name.


scope 提供 $watch $apply $on $emmit 等api

--额外解释
    angular的双向绑定,是dom和数据之间的双向触发,那么可以用$watch来监听数据变化, $apply来执行dom变化
    $on $emmit是事件类型的,通知,监听 类似于addEventListener dispatchEvent(trigger);
    
scope 可以在提供到被共享的 model 属性的访问的时候，被嵌入到独立的应用组件中。 scope 通过（原型），从 parent scope 中继承属性

scope 在 expression 求值之时提供上下文环境,比如,ng-class="{active:tab==1}"  当tab为1的时候,当前的class为active
那么ng-class的这个表达式,其中的scope,就是tab的上下文指向.

https://jsfiddle.net/igaves/1jueaLpy/

看一下例子,例子上操作了一个name,一个tab,那么在表达式中,他俩都并没有用as的形态来做,那么他俩数据的指向,都是scope



##as操作符

as,是为了多个controller嵌套区域,可以横向引用的一个方式.

比如
    <div ng-controlelr="controllerA as a">
    
        <div ng-controller="controllerB as b">
            {{a.title}}
            {{b.title}}
        </div>
        
     </div>

这样,就避免了,在controllerB的区间内,访问a的title混淆概念


>本节内容应该就是纯粹的演示行为,核心就是理解scope概念,下一节,就是自定义directive,是最难理解的.







