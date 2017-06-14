---
layout: post
title:  Node／typescript 接入Decorator
date:   2017-03-03 08:59:59
categories: it
summary: >
    TS 接入Decorator 是对开发力量很节省的一个做法
---

装饰器java／as3编程中经常用到，在ts项目中，可以轻松做到简约无业务代码影响的情境下进行装饰性上报逻辑

```typescript

    @Log('network')
    private sendToQueen(){

    }

```

解耦很方便。

前一阵写了个 https://github.com/igaves/angular-restful-service

angular是我最近的学习目标。

不仅限于怎么用，而是研究它的思路，和设计方法。
