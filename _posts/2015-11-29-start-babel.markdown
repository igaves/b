---
layout: post
title:  Babel,给JS进化加一把火
date:   2015-11-29 20:21:30 +0800
categories: developer 
paid: yes
---

>这玩意以前叫6to5
>就是把ES6的东西编译成ES5，也就是说，可以快速进入新的语法逻辑，而且可以兼容旧的浏览器

这个重要性不言而喻，其实ES6的语法改版，就是为了推进前端的进化。

新的开发方式。

回顾当年Ajax狂潮，其实技术很早就有，然后突然的这种开发方式对整个的互联网进行了全新的诠释，用户体验这个词汇应运而出。

先说下莫大认为的重要性几点

    function A(){
      this.load();
    }
    A.prototype.load= {
      //当属于A的dom被点击触发事件拉取
      domBelongToA.onclick=function(){
        Service.loadData().done(B.reDraw);
      }
    }

    function B(){
    }
    B.prototype.reDraw = function(data){
      //重会B的页面显示
      domBelongToB.render(data)
    }

可以看到，其实，AB两个对象之间，是相互依赖的，而且页面属性也是纠缠的。
不得不说，这就是现在的最常用的开发方式

即便我们用angular，也得通过一个Service来进行数据的传递

    angular.module('app').service('loader',['$http',function(){

        return {
          data:{},
          load:function(){
            var _this = this;
            $http.get().done(function(res){
                _this.data = res.data;
            })..
          }
        }
    }]);

    angular.module('app').controller('A',['loader',function(loader){

        this.load = function(){
          loader.load();
        }
    }]);

    angular.module('app').controller('B',['loader',function(loader){

        //loader infect
        
    }]);


这个是却是很传统的方式，数据的流向，必须有一层桥接(angular的设计思路已经很先进了)，活着嵌套引用。
谈什么设计模式。

A其实就是个界面操作，B也是界面操作，那么肯定要进行比较规范化的拆分，界面，数据等等

    export interface IHttpRequest{
      loaded(res:object):void;
      error(res:object):void;
      request(promise:Promise):Promise;
    }

    class Loader {

      function addEventListner(name:string,handler:IHttpRequest){
        var http:Http = new Http();
        http.url = 'xx';
        //不封装了，其实这里可以HTTP内包含接口实现,写出来参考而已
        http.get(IHttpRequest.request)
          .success(IHttpRequest.loaded)
          .error(IHttpRequest.error);
      }
    }

    export class B{

        [selector="domBelongToA"]
        click(event:Event)(
           var loader =  new Loader(); 
           //此处用接口类型解
           loader.addEventListner('loaded',this);
           loader.load();
        )

    }


其实用这中方式，新手老手都必须走一条强行实现接口的过程，
那么基本上可以保证质量维持在一个范围内。

那么也就是说，babel最深入的意义并不是语言之间的转化，而是期望于语言之间的转化，能引入新的开发方式。

##前端开发者的困境

纵观前端开发者，基本上都是快餐式开发，左手一个搜索引擎，右手一个浏览器开发者工具
代码不会写上网一搜，页面有问题，就哪里不行点哪里，实在不行卡个断点，so easy。

回头想象，我们开发渐渐趋向于一个*尝试性开发*
那么java是怎么来做的呢，因为编译性语言，总归写几个字，就编译一下调试吧。。

**稍等，今天我去采访一下前IBM测试开发工程师，现在的小米金融大数据开发工程师去，这是我同学，我不能瞎喷。。采访完贴内容。**


未完待续。。 只写半小时，剩下的时间写代码。。
要是想催更新，快收听。


