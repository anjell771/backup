[TOC]

# 个推开发者平台创建应用
##1、  打开 [个推开发者平台](http://dev.getui.com/dos4.0/index.html#register) 注册成为开发者
![](http://newdocx.appcan.cn/docximg/145412q2015d5a1g.png) 

##2、 注册成功后登陆并登记应用
Android 应用标识填写自定义的包名。
iOS 应用证书选择导出的 p12 格式推送证书，密码为导出时创建的密码。
![](http://newdocx.appcan.cn/docximg/145517k2015p5g1u.png) 

##3、  打包个推插件
###3.1  自定义插件包（只针对安卓）
下载个推插件包 Android 版本，解压、修改 AndroidManifest.xml。

将登记的应用配置信息 AppID、AppSecret、AppKey 分别对应替换 AndroidManifest.xml 中的 appId、appSecret、appKey。
替换 packageName 为自己定义的 Package Name。
![](http://newdocx.appcan.cn/docximg/145747d2015q5w1e.png) 

修改完成后压缩打包，作为自定义插件上传到打包服务器。

##4、在线打包
####4.1 ×选择上传到打包服务器的自定义插件
![](http://newdocx.appcan.cn/docximg/150030w2015l5c1g.png) 

####4.2 ×选择证书填写自定义包名进行打包（安卓）
![](http://newdocx.appcan.cn/docximg/150046b2015w5s1u.png) 

 ####4.3 × ios应用需要上传申请的苹果证书，打包选择对应的证书
 如下图
![](http://newdocx.appcan.cn/docximg/170213f2015v5m5r.png) 
![](http://newdocx.appcan.cn/docximg/170451v2015c5u5z.png) 
最后， [跳转](http://dev.getui.com/dos4.0/index.html)到个推开发者平台，创建推送