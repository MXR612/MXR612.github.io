---
ID: 22
post_title: Hello, world!
post_name: hello-world
author: mxr612
post_date: 2021-03-14 00:03:36
layout: post
link: https://mxr612.top/?p=22
published: true
tags: [ ]
categories:
  - 随笔
---
<h2>基本上是个建站记</h2>

但是本文没有任何技术指导QwQ

其实前后搞了两次，用时一周吧。第一次是在Ubuntu Desktop上面建的，中途出了好多差错，系统也乱七八糟了。最后决定下单一块树梅派，专机专用。

实在是非常难熬的一周，晚修完全没办法专注，作业都没怎么能完成。这一周拼命挤时间查阅各种博客，星期三因为没有看清文档（加之功夫不到位）在没有把frp开机自启的情况下重启了我的Ubundu Desktop。

到手之后直接下载树梅派官方的烧录程序，从烧录程序里面直接下载Ubuntu Server的img。也许对于小白来说，官方的就是最好的，毕竟保证一次点亮。虽然之前是想安装arch的，没有在树梅派官方源里面，感觉有点麻烦了。

点亮之后用路由器找剩余租期最长的一个设备，然后直接设为固定ip，加DMZ。SSH进去之后默认帐号密码都是ubuntu，修改密码之后就能正常使用了。

<h2>Wordpress&amp;插件</h2>

参照各种教程以及自己的记忆安装和配置了Apache2，php，mysql。从官网下载的wordpress，跟据php文件直接建起，没什么多说的。

建起之后常规的Jetpack搞了，然后尝试了各种各样的wordpress-github的markdown同步插件，未遂。最后选择了WD Editor.md，打算以后都先在本地编写然后手动复制到wordpress上。

<h2>Arch linux</h2>

本来的Ubuntu早就想换了，工作日也查了很多文献，熬了一晚装了两次成功点亮。