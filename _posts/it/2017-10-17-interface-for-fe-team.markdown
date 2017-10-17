---
layout: post
title:  Interface在项目中的思考
date:   2017-10-17 08:59:59
categories: it
summary: >
    接口在中台项目设计中的作用，是保障多人协作时候，可以在同一个思考线上
---

举个例子， 系统中，对于资源的连续加载有很多，基本上分为

1. 分页
2. 加载更多／瀑布流

所以，后台系统中，前后端都应该统一约定一个 接口定义来约束

``` typescript
interface Pager{
  total?:number;
  page?:number;
  size?:number;
}
```
这是对分页的基本约束，那么对Response的约束，可以给予接口去扩展

``` typescript
interface ResouseResponse<T>{
    code:number;
    message:string;
    pager:Pager,
    data:T[];
}
```
接口协议清楚，那么保证resource资源都是可数组化的返回，那么我们创建了一个通用组件:
(设，video-tile是视频块组件)
**PaginationGrid**

普通分页


```html
<pagination-grid [source]="'/api/userVideo'" [size]="20" #video_list>
    <video-tile *ngFor="let video of video_list" [video]="video"></video-tile>
</pagination-grid>
```
![分页方式](http://km.oa.com/files/photos/pictures//20171012//1507806774_52.png)


也可以快速切换为加载更多
```html
<pagination-grid [source]="'/api/userVideo'" [size]="20" [method]="'LOAD_MORE'" #video_list>
    <video-tile *ngFor="let video of video_list" [video]="video"></video-tile>
</pagination-grid>
```
就可以达到
![加载更多](http://km.oa.com/files/photos/pictures//20171012//1507806345_76.png)



分页不再像传统的方式，控制页码各种事件，直接实现**约定接口**，即插即用。

所以，直接砍掉了开发资源，才是组件化对项目的提升。


加载更多和分页共用一套response不讨论，但是接口化协议，对前端组件化处理会有很大的推进，组件复用阶段毋需从数据协议转化阶段考虑，只需要考虑遵循接口。

**
所以typescript成为前端开发标配很有意义，可以让前后端都在同一套接口约定下进行开发
**
前后端接口统一，项目才更健壮。