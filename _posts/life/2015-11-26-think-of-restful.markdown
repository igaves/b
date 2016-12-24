---
layout: post
title:  "Restful 设计在开发中的价值"
date:   2015-11-25 23:21:30 +0800
categories: developer 
paid: yes
---


先说明一句，我这个是markdown写的，加图得自己切，我比较懒，就少一点图了。
但是no pic say a bird.

>A：前端，B：后端

###场景：

>A:"哥，我要请求文章信息的

>B: "好的，稍等"

>http://domain.com/api/getArticle?id=11

>http://domain.com/api/updateArticle?id=11

>A:"哥，来个文章列表的吧"

>B:"好的，稍等"

>http://domain.com/api/aritclesist

>A:"哥，来个文章下评论的接口吧"

>B:"好的，稍等"

>http://domain.com/api/getComment?article_id=11

>"哥，差不多了，所有的接口功能我都对上了。"

>"上线吧！"

###场景二

>A:"哥，文章，评论两个资源搞定一下"

>B:"好的"

>"{articles|comments}done, comments belongs_to article "

>B:"哥，搞定了，上线吧";

>用到功能

>/articles

>/articles/11

>articles/11/comments 

>操作CURD /articles/11


好的，我们根据上述两个场景，先简单讲述第一个优势

###API应该对程序员友好,具有自释性

首先搞定的一件事，就是前后开发同学，对于协议的定制在业务之前就已经有初步的约定了，就是resource资源描述

- 首先，API描述资源，不需要动词来解释用途

- 再次，API接收HTTP动作(POST,GET..)，进行对应的用途指引

- 最后，用API层级描述，来表达资源之间的关系

这样做，最大的好处，就是无论新手，还是老员工，都可以在理解restful设计理念的基础上，无缝的切入业务开发的洪流之中，不需要进行很多接口文档的研读，新业务也不需要提前敲定接口协议，即可进行前后端联合开发

###API对于系统开发友好，可快速抽象业务逻辑

这个最直接的体现，就是很多框架，库的实现呵呵哒。

未完待...










