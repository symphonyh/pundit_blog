---
layout: post 
title: Rails Routes 
date: 2017-03-13
comments: true
external-url:
categories: Rails
---

Rails 路由会通过你配置的路由规则将发送来的 URL 分发到对应的 action 中。它同时会生成 paths 和 urls 来避免你在视图中使用硬编码。
>

```
resources :events

```
<!--
<img src="/image/routes.jpg" width = "710" alt="Rails RESTful 标准路由" /> 
-->

默认情况下，rails 会为每一个 RESTful 路由建立 7 个`action`:

| Helper| GET | POST | PATCH | DELETE |
| :------ | :------ | :------ | :------ | :------ |
| event_path(@event) | /events/:id   `show` |      | /events/:id `update`| /events/:id `destroy` |
| events_path | /events`index` | /events `create` |   |      |
| edit_event_path(@event) | /events/:id/edit `edit` |   |   |   |
| new_event_path | /events/new `new` |  |   |   |



rails 在默认情况下，会为每一个 RESTful 路由建立7个动作，并且生成对应 Helper:相对路径的`_path`,绝对路径的`_url`。加了HTTP动词的路由简化成单数和复数两类,`event`。

复数形式:`events` 

`events_paht => /events` 

复数的 events_paht 对应的 action为 GET：`index` 和 POST：`create`；只有两个，且HTTP动词也不同所以`events_path`不用参数rails就能区分 action。

单数形式:`event`

`event_path(@event) => /events/:id`

对应不同的HTTP动词：

1. GET 对应action为：`show`
2. PATCH 对应action为：`update`
3. DELETE 对应action为：`destroy`

Helper名称都是`event_path`需要用参数`@event`的实例变量传递要show、update 或 destroy 处理的参数;

对于GET动词还有两个action，区分的办法是在前面加前缀 `edit` 和 `new` ：

 `edit_event_path(@event) => /events/:id/edit`
和
 `new_event_path  => /events/new`

<hr>

```
resource :session, only: [:create, :destroy]

```
单数资源路由最常用的例子就是session

|--------------------|-----------|------------|
| Helper               |POST       |  DELETE     |
| session_path   |/session |   /session  |
|                | sessions#create    |    sessions#destroy  |
 
<hr>
###  参考:
有了上面的基础，关于路由的知识参考这两篇文章:

1、[Rails 路由学习笔记](http://www.jianshu.com/p/Ro4HZT) 
2、[Rails路由使用](http://www.jianshu.com/p/6a24f0665bb0)