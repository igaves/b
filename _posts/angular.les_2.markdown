---
layout: post
title:  Angularjs Lesson 1
date:   2016-01-03
categories: angular
---
#>我们先要了解一下angular项目的基础概念

app,module,controller等,app是程序入口,module是对于功能模块性的拆分定义,controller就是对于界面的控制部分


OK,到现在阶段,大家应该对angular有了一个了解

接下来就需要了解一下angular几个基础概念

首先一个webapp,必然需要一个入口函数,那么这个入口,可以写成_ng-app_


    <div ng-app="MyApp" ng-controller="DemoController as ds">
    
        <ul id="list">
            <li ng-repeat="item in ds.list" id="item_{{item.id}}" ng-show="item.available">
                {{item.content}}
            </li>
        </ul>
    
        <button ng-click="ds.addItem()">添加一项</button>
    </div>
    
    


##首先代码中我们必须定义一个module,

    angular.module('MyApp',[]);
    
这就是我们程序的入口,扩展一下,在这个模块内定义一个controller

    var app = angular.module('MyApp',[]);
    
    app.controller('DemoController',function(){
        ...
    });


写法很简单,先定义模块,在模块下,定义controller即可

所以,模块的概念就是:
    ###angular中,按照代码抽象功能,进行的明明空间的拆分.
    
再举例!

如果网络上有人写了个angular的拖放扩展功能,那么我们怎么用?

比如https://github.com/codef0rmer/angular-dragdrop

首先,比较确定的,这个必然是一个模块,那么我只需要注入这个模块即可!
    
    var app = angular.module('MyApp',['ngDragDrop']);
    
    
可以看一下这个源代码,它在代码最前面,必然声明了自己的模块名称,然后代码逻辑在此模块内进行开发

https://github.com/codef0rmer/angular-dragdrop/blob/master/src/angular-dragdrop.js


有了模块,我们就可以在模块下进行逻辑开发

##controller,是把DOM片段中的指令,和非显示性元素逻辑联系起来的代码段,也叫angular中的控制器

好了,我们在模块下,进行controller的定义
    
     var app = angular.module('MyApp',[]);
     
     //首先我们定义一个函数
     function DemoController(){
     
     }
     //在声明controller名称,然后指定为上面这个函数
     app.controller("DemoController",DemoController);
     
     当然,我们也可以用匿名函数的方式来声明
     
     app.controller("DemoController",function(){
        
         this.addItem = function(){
            //do some thing
         };
     });


dom这个controller下的指令逻辑,都可以定义.
我们在这个controller下,定义了一个函数_addItem_;

(在这里,要重点演示一下,怎么把指令中的方法,写到dom上,并且运行出来预期结果,比如打一个alert);


那么就剩下angular中最后一个(强调一下就这么多东西了,可以减少听众心理压力)很重要的概念Service

#angularjs中,这概念为非显示元素逻辑处理的定义模块

比如很多网络请求,ajax,各种数据的处理都可以放在FSP中进行定义.

这个很重要,能帮助我们把controller的复杂度降低下来,想象一下,我们把操作DOM的代码逻辑和ajax请求后成功失败处理,混写在一块,从维护角度,这绝对不是前端开发中的最佳实践.

所以,angular提供了我们Service的概念.

  1.Factory
  2.Service
  3.Provider
  

>Factory 就是创建一个对象，为它添加属性，然后把这个对象返回出来

    app.factory("webPage",function(){
        
        var _web_page =  {
            title:'文章标题'
            content:"文章内容",
            updateTitle:function(){
                this.title = "文章更新后的标题";
            }
        }
        
        return _web_page;
    });
    

好的,我们可以注入到controller中去用了

    app.controller("DemoController",function(webPage){
        
        this.alertPageTitle = function(){
            alert(webPage.title);
        }
    });
    
    
>Service 是用"new"关键字实例化的

    app.service('webPage',function(){
        this.title = "文章标题";
        this.content = "这个是文章内容";
    });
    
    

>Provider Providers 执行一次,且 $get 访问定义内容

    app.provider("webPage",function(){
        
        var _config = {
            charset:'utf-8'
        };
        
        
        this.$get = function(){
        
            return {
                title:"文章标题",
                content:"文章内容"
                config:_config
            }
        }
    });
    


https://jsfiddle.net/igaves/7xnjwma3/3/