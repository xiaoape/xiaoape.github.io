---
layout: post
title: 静态页面和动态页面的区别
categories: Markdown
description: 静态页面和动态页面的区别
keywords: Markdown, VSCode
---

## [静态页面和动态页面的区别](https://www.cnblogs.com/bluesungz/p/5955170.html)

 

一、静态web页面：

1、在静态Web程序中，客户端使用Web浏览器（IE、FireFox等）经过网络(Network)连接到服务器上，使用HTTP协议发起一个请求（Request），告诉服务器我现在需要得到哪个页面，所有的请求交给Web服务器，之后WEB服务器根据用户的需要，从文件系统（存放了所有静态页面的磁盘）取出内容。之后通过Web服务器返回给客户端，客户端接收到内容之后经过浏览器渲染解析，得到显示的效果。

2、为了让静态web页面显示更加好看，使用javascript／VBScript／ajax（AJAX即“Asynchronous Javascript And XML”（异步JavaScript和XML），是指一种创建交互式网页应用的网页开发技术。）但是这些特效都是在客户端上借助于浏览器展现给用户的，所以在服务器上本身并没有任何的变化。

3、静态web无法连接数据库；

4、静态web资源开发技术：HTML；

5、由于现在的web页面中，大量使用JS，导致浏览器打开页面，就会占用大量的内存，服务端的压力是减轻了，但压力转移到了客户端。

 

 

二、动态web页面：

动态WEB中，程序依然使用客户端和服务端，客户端依然使用浏览器（IE、FireFox等），通过网络(Network)连接到服务器上，使用HTTP协议发起请求（Request），现在的所有请求都先经过一个WEB Server来处理。

如果客户端请求的是静态资源(*.htm或者是*.htm)，则将请求直接转交给WEB服务器，之后WEB服务器从文件系统中取出内容，发送回客户端浏览器进行解析执行。

 

如果客户端请求的是动态资源（*.jsp、*.asp/*.aspx、*.php），则先将请求转交给WEB Container(WEB容器)，在WEB Container中连接数据库，从数据库中取出数据等一系列操作后动态拼凑页面的展示内容，拼凑页面的展示内容后，把所有的展示内容交给WEB服务器，之后通过WEB服务器将内容发送回客户端浏览器进行解析执行。

![img](https://images2015.cnblogs.com/blog/1035591/201610/1035591-20161013090832625-143100190.png) 

再进一步深入分析动态web的访问过程：浏览器访问web时，看似是直接访问的jsp页面，其实是，最先到达的地方是服务器，服务器创建好req和resp对象后再给jsp页面使用。在jsp中完成设置字符集和取得表单参数后再调用servlet，完成业务处理。然后返回到jsp，jsp就会生成相应的html页面。该页面会返回到服务器，再由服务器，通过response对象返回给客户端。 

![img](https://images2015.cnblogs.com/blog/1035591/201610/1035591-20161013090850453-1606322464.png) 

为什么需要web服务器？(web server)
1）不管什么web资源，想被远程计算机访问，都必须有一个与之对应的网络通信程序，当用户来访问时，这个网络通信程序读取web资源数据，并把数据发送给来访者。
2）WEB服务器就是这样一个程序，它用于完成底层网络通迅，处理http协议。使用这些服务器，We应用的开发者只需要关注web资源怎么编写，而不需要关心资源如何发送到客户端手中，从而极大的减轻了开发者的开发工作量。

 三、关于两者区别的简单直接的描述
1、静态页面就是设计者把页面上所有东西都设定好、做死了，然后放上去，不管是谁在任何时候看到的页面内容都是一样的，一成不变（除非手动修改页面内容）。静态html页面文件，可以直接用本地的浏览器打开。比如：file:///Users/Phil/Documents/DevOps/HBuilderProjects/testJSP/index.html。
2、动态页面的内容一般都是依靠服务器端的程序来生成的，不同人、不同时候访问页面，显示的内容都可能不同。网页设计者在写好服务器端的页面程序后，不需要手工控制，页面内容会按照页面程序的安排自动更改变换。