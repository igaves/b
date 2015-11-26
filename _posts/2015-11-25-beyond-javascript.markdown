---
layout: post
title:  "前端的未来，写在Angular和React火热之际"
date:   2015-11-25 23:21:30 +0800
categories: developer 
paid: yes
---

其实从Angular大改版到Angular2，我就预感到了，真正的Web 和 Mobile的融合即将到来。

周末我特别无聊的，翻腾出了自己三年前的代码重新看了一遍，当时自己实现了很多好用的方法，比如

{% highlight javascript %}
setTimeout(function(){xxx},1000);
{% endhighlight %}

改写成了

{% highlight javascript %}
function(){}.delay(1000);
{% endhighlight %}

delay的实现，完全依赖了回调函数的处理。

后来经历了jQuery的改版，其中引入了Deffered（Promise）实现

始终感觉到，这只是在目前简陋的开发条件下（javascript）的一种扩展实现，代表不来前端的未来，异步处理过程，对前端来讲，是复杂度的根源


后来前端框架雨后春笋，从Backbone到近两年的Angular出现，逐渐的，MVC的概念已经逐步的扩展到了MVVM,又经历了Angular团队对Angular彻底推翻进行Angular2开发，明显的感觉到，其实前端这个行业已经不再是以前意义的前端行业了

那么可以简单的去写，2015年，是一个分水岭，15年之前，是前端开发，搞js，html的，15年之后，是真正的人机交互开发，是搞组件，搞控件，搞工程化众包开发的。

不好理解？

那么可以理解一个真正的历史

>AS2和AS3
>是一个完全基本OOP的标准化面向对象语言，最重要的就是as3不是as2的简单升级，而完全是两种思想的语言，不兼容。

AS2，都是在控制Flash中的元件，Flash中的素材，但是到了AS3，基本上都是层层继承，面向接口去定义所有的对象，AS2开发，基本以设计居多，但是AS3开发人员中，很大一部分，都是类JAVA开发转居多。

返回说前端，15年之前，大家应该还是在运用选择器，选择DOM，进行DOM的状态切换组合，事件监听等等，但是未来的开发，应该都是基于组件体系的一个控制流，譬如控件与数据流之间的通信，未必会全部基于Http/s协议，也有WS，本地Cache&Store存取，即便给予Http，那么也有Web Workers的Thread并发概念，数据处理完全可以从页面渲染流程中脱离，

那么再说一下Rxjs的概念，这基本上都是Observable Sequence的概念，相互订阅通知，根据状态的切换来进行不同的处理方式，而且，这种组件&组件之间或者组件&数据之间的通信，很容易写成隐形的封装。

Angular1.x基本上也是类Flex的给予Observable的设计理念，但是，目前的ViewModel之间的状态切换，还是依赖于Event&Listener  Callback&Promise实现的通信协议，就是Dirty Check逻辑，当然，这样能够为你的模型使用纯老式的JavaScript对象。

Angular2，其实真正的改变，并非框架版本号从1.x到了2.x，也并非切换到Typescript，也并非号称的组件化模块化响应，也不是装饰化声明（Meta？

*而是理念的改变*。

这对90%的前端开发，基本上都是很痛苦的折磨。

尤其是，这种开发思路，其实可以无限制的放大到Application For Desktop上。

当打开一个人机交互页面，思考一下操作流程：

当我点某个按钮的时候，打开某个窗口，展示什么内容，这一切怎么转化成程序描述语言？

难道还是 Query.on event do function ?


###React打算咋办

React本身就是一层抽象的表现层，在我的理解，它只是解决了一层很显示的方案，并且在此方案上拓展到了hybird 层面：原生应用混杂编程。
不过我依旧不看好如此开局，毕竟前端的真正的核心之一就是强大的CSS排版引擎。
React太过于强调视觉抽离和界面抽象，甚至模拟出来了lite版本的css，但是毕竟在整个行业的解决思路上距离Angular2的设计理念还有很远的距离。

React提供了一种很强化的思路，强调于数据单流向，但是没有对整个行业带来很深入的改变。数据本身来讲，就是一个整体，html仅仅是一个排版引擎，html和css应该是一体思维，但是jsx混杂了html＋脚本，但是忽略了CSS这个排版引擎。

在我看来React＝(javascript+html)+css angular＝javascript+(html+css) 双方侧重点不在一个层面，引入了babel后，未来开发会有不同流派

我站在Angular2一边，甚至我认为inoic开发思路未来不仅限于mobile，angular2也应该是Desktop & Mobile Application的解决方案

但是React仅仅是View方案。that's All


未完待...




