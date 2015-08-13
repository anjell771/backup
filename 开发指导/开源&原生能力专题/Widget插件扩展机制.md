[TOC]

###  1、功能描述
  通过AppCan平台生成的应用，可以理解为一个Widget包（即在IDE创建项目是看到的'phone'文件夹），和一个 AppCan平台中间件组成的。通常的情况下，一个应用是由一个Widget+AppCan构成，那么，有没有可能说'n个Widget+AppCan' 的机制呢，答应是肯定的，这就是Widget 插件机制，是针对主widget以及普通widget 的一种增强性的扩展机制，可以将具有特定功能的widget封装成一个单独的widget包存放到plugin 下，然后通过js扩展接口调用，以达到功能扩展的目的。我们把'1个Widget+AppCan'中的那一个Widget叫做'主Widget'，而另外 的'n-1'个Widget存在于主Widget的'plugin'目录下。
  
**视频案例**:  [百度地图插件开发（安卓）][百度地图插件开发（安卓）]

### 2、目录结构
  Widget 插件包存在于当前主widget下的plugin 文件夹下，按照widget包名依次排列，插件widget 命名是以'appId'作为文件夹名称（比如'10031466'），插件widget里面的目录结构跟主Widget类似（除了没有'plugin'目 录，即插件widget中没有二级插件widget）。
![](http://newdocx.appcan.cn/docximg/141456u2014x8p26r.jpg)

Plugin文件夹 ：存放plugin widget 包；

### 3、插件调用
**StartWidget接口**

可以实现widget和widget之间进行数据传输，以及注册callback函数
【参考插件 API】

**finishWidget 接口**

参数为该widget 插件关闭传给调用该widget 的数据，正好回应了startwidget 接口中的callback方法
  【参考插件 API】

### 4、其他接口

  平台的所有接口都可以调用，如果有对文件读写或者拍照等等数据存储接口的调用，数据存储的位置与调用该插件的widget 的数据存储位置一致。
[百度地图插件开发（安卓）]: http://player.letvcdn.com/lc01_p/201505/26/09/25/18/newplayer/bcloud.swf?uu=8ab2042bd4&vu=365e2611cc&auto_play=1&gpcflag=1 "百度地图插件开发（安卓）"