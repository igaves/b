---
layout: post
title:  一个错误的webview页面长连思路
date:   2016-06-11 12:59:59
categories: developer
---

###突然有了个想法
demo如下
起了一个ws请求连到了后台
    ....
    var ws = new WebSocket("ws://demo.igaves.com");
    ws.onmessage = function(evt){
        let flag = evt.data.flag;
        sendMessageToView(flag,event.data);
    };
    
    
有这么一步后,我在进入页面就建立了连接,然后,直接发送当前的行为tag,server 端把本tag所有必备数据,全部加工好发过来.

    ws.onopen = function(){
        sendActionTag(pageTag);
    }
    
demo完成,基本上就是用socket替代了http的逻辑.

然后,仔细思考下.
对于请求本身,建立一次socket连接,和多个http连接,哪个资源成本更高?

1. socket当然秒杀http喽..不过socket是长时间连接的,http是分散请求的,峰值压力,某些业务下,http很可能是碾压socket的.
2. 缓存这事就没辙了..socket只能人肉缓存.低效,http可以充分利用http协议来做缓存控制.
3. 无缓存的情况下,如果是实时数据处理,集中性的数据业务,socket可能更漂亮.比如web im?呵呵这个例子不恰当.

欧克,看一下server端处理吧..

    article = Article.find_by_id params[:id] //from mysql & redis
    sendWs(:article,article);
    user = User.mine(); //read session(redis) & mysql
    sendWs(:user,user);
    
仔细一看,server端损耗基本上在网络IO之上,其次是sendWS中对于ruby对象的json化.

其实有了ws之后,传统的网络方式未必靠谱了..果断EM(这里果断切node也是合理的)

其实,避开网络IO实效损失才是应做的.

继续思考.

我上了http2.0,那么多个http,其实是走的一个连接通道.
那么我纯的想法,在可缓存的应用上,基本上就是被废掉了.

那我又有了个新想法,
想避开网络IO损耗,其实异步长连还是有用的.
但是IO损耗避免不了,总归需要代理层来解决一些缓存问题.
加了代理层,其实也无所谓什么node什么了..只要不雪崩,就好.





    
    
    