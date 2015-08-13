AppCan IDE为开发者提供了Android和iOS平台真机同步调试功能，只需在同一wifi环境下，部署到真机上的应用就可实现与PC端的实时同步调试功能，帮助开发者高效率、便捷的调试应用。

[TOC]

### 1、真机同步调试
1）、配置要调试应用的Config文件，选择调试服务器地址，勾选"真机同步调试"。
![](http://newdocx.appcan.cn/docximg/161721g2014u11v4n.png)

2）、项目打包，安装至手机（iOS安装需越狱设备）。
（注意：真机调试必要条件：设备与pc必须在相同网段）判断方法：在设备浏览器里输入“192.168.1.213：30060”看一下访问的页面是否是下图的页面，如图：
![](http://newdocx.appcan.cn/docximg/161948h2014r11q4f.jpg)

3）、点击"启动真机同步调试服务"，启动手机端应用。
![](http://newdocx.appcan.cn/docximg/144535y2015g5u29g.png)

4）、点击需要调试的页面。
![](http://newdocx.appcan.cn/docximg/144549q2015k5q29o.png)

点击后进入如下图的所示的调试页面：
![](http://newdocx.appcan.cn/docximg/132340m2015f1g28g.jpg)

5）、手机端与PC端可实现实时调试。
![](http://newdocx.appcan.cn/docximg/143608i2015a5g29y.png)

在调试窗口中修改某处css样式，真机可实时同步看到效果PS:在调试窗口修改的东西是不能直接缓存到真机上，只是达到调试预览修改后的效果；需要重新打包，装到到手机才能看到调试后的效果。
![](http://newdocx.appcan.cn/docximg/143713x2015q5x29m.png)

效果图：模拟器上操作
![](http://newdocx.appcan.cn/docximg/132243x2014n10w12b.jpg)

调试的同时注意看手机上的效果变化，如图，
![](http://newdocx.appcan.cn/docximg/101315v2014m10e12k.png)

### 2、AppCan调试中心
#### 2.1、生成AppCan调试中心
AppCan调试中心是AppCan IDE为开发者提供的一款可真机同步调试的门户应用，只需通过网络部署子应用（需测试的应用）后，无需二次打包，就可实时测试修改应用。
点击"生成AppCan调试中心"。
![](http://newdocx.appcan.cn/docximg/172432g2014f9v22q.jpg)

进入AppCan调试中心打包流程：
设置应用名称及icon。
![](http://newdocx.appcan.cn/docximg/135924g2014d9p23z.jpg)

点击"下一步"，设置平台、启动页。
![](http://newdocx.appcan.cn/docximg/135935z2014q9y23y.jpg)

点击"下一步"，选择插件。
除默认已选插件外，还需选择要部署的子应用中用到的插件。
![](http://newdocx.appcan.cn/docximg/135945q2014p9p23p.jpg)

点击"完成"，打包成功。

将AppCan调试中心安装至手机（iOS安装需越狱设备）。
![](http://newdocx.appcan.cn/docximg/140004q2014r9u23v.jpg)

安装AppCan调试中心。
![](http://newdocx.appcan.cn/docximg/172749n2014w9d22h.jpg)

#### 2.2、启动AppCan调试中心服务
在PC端，启动AppCan调试中心服务。
![](http://newdocx.appcan.cn/docximg/172824f2014g9n22g.jpg)

#### 2.3、使用AppCan调试中心
启动手机端AppCan应用调试中心。
![](http://newdocx.appcan.cn/docximg/103623g2014l10s12b.jpg)![](http://newdocx.appcan.cn/docximg/103636e2014n10i12k.jpg)![](http://newdocx.appcan.cn/docximg/103651w2014y10c12m.jpg)

点击"开始使用"，进入登录页。
调试需要在同一WIFI下进行，输入同步PC端的IP地址，注意关闭防火墙，点击登录。
![](http://newdocx.appcan.cn/docximg/173259p2014e9p22n.jpg)

主页面，IDE中左侧导航列表应用均会显示在首页。
![](http://newdocx.appcan.cn/docximg/103941l2014m10y12c.jpg)

点击，进入需要调试的应用。
如有需修改，可编辑IDE中代码，然后在当前应用中点击右下角小球，退出到首页，再次点击应用进入，方可看到修改后效果。

#### 2.4、启动真机同步调试服务
点击"启动真机同步调试服务"，流程同[真机同步调试](#1、真机同步调试) 一致。