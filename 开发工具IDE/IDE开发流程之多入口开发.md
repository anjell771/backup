随着移动互联网的爆发，入口之争愈演愈烈。从大的趋势看，App、Web、微信成为最火热的三大入口。这给移动开发者和移动创业者带来新的考验，需要考虑多个入口下的开发与管理。
顺应这种趋势，AppCan全新升级IDE系统，为开发者提供全入口开发支持，即一次开发，多平台，多入口，全适配。基于AppCan新版IDE，开发者可一键生成App、Web/微信 App两种形式，轻松应对市场需求，在竞争中更胜一筹。

[TOC]

####1、使用范围
当您的应用中仅涉及到了以下方法，均可支持生成Web/微信 App。
>uexWindow.open
uexWindow.cbOpen
uexWindow.close
uexWindow.cbClose
uexWindow.closeByName
uexWindow.openPopover
uexWindow.closePopover
uexWindow.setPopoverFrame
uexWindow.setBounce
uexWindow.refreshBounce
uexWindow.evaluateScript
uexWindow.evaluatePopoverScript
uexWindow.alert
uexWindow.closeAlert
uexWindow.confirm
uexWindow.toast
uexWindow.closeToast
uexWindow.actionSheet (buggly)
uexWindow.cbActionSheet
uexWindow.bringPopoverToFront

另外，想要使用微信接口，需要后端提供一个签名服务器（该版面提供nodejs 版本），并且再所有用到接口的页面进行签名否则所有接口失效，该版本提供一个setWeiXinConfig(url)方法，进行自动签名，URL是签名接口的完整路径。
已兼容接口：
>· startRecord <==> uexAudio.startBackgroundRecord
·         stopRecord <==> uexAudio.stopBackgroundRecord
·         onVoiceRecordEnd <==> uexAudio.cbBackgroundRecord
·         playVoice <==> uexAudio.open && uexAudio.play
·         pauseVoice <==> uexAudio.pause
·         stopVoice <==> uexAudio.stop
·         onVoicePlayEnd <==> uexAudio.onPlayFinished
·         chooseImage <==> uexImageBrowser.pick && uexImageBrowser.pickMulti
·         previewImage <==> uexImageBrowser.open
·         getNetworkType <==> device.getInfo('13')
·         openLocation <==> uexBaiduMap.open && uexBaiduMap.setZoomLevel && uexBaiduMap.setCenter
·         getLocation <==> uexBaiduMap.getCurrentLocation
·         scanQRCode <==> uexScanner.open
如想用微信其他接口，可自行封装。

#### 2、使用方法
在IDE中应用开发完成后，如要生成Web/微信 App，需先配置当前应用的config.xml文件，勾选”Web/微信 App”选项并保存；
![](http://newdocx.appcan.cn/docximg/151329p2015d2e23o.png)

> 注：勾选“Web/微信 App”后，请避免使用页面实时预览、模拟器调试及svn代码上传功能。如想使用，请提前在config.xml文件中勾掉不选。

在当前应用中选择phone目录右键，
![](http://newdocx.appcan.cn/docximg/151355q2015c2c23w.png)

1）、选择“启动Web/微信 App服务”，可启动本地服务在内网中预览应用效果，此时控制台会显示本机IP及端口
![](http://newdocx.appcan.cn/docximg/151416k2015t2h23u.png)

在手机浏览器或微信中输入或扫描IP+端口地址，直接预览应用效果；
![](http://newdocx.appcan.cn/docximg/151435r2015c2e23m.png)

2）、选择“生成Web/微信 App”，在安装目录中的WebApp-Applications中生成一个zip包
![](http://newdocx.appcan.cn/docximg/151451m2015l2n23i.png)

将zip包部署至外网服务器即可访问。

3）、项目开发完成后需要部署到服务器上才能访问，首先你需要一台外网机器，以我的测试机器为例，登录到服务器上
![](http://newdocx.appcan.cn/docximg/151511e2015i2q23k.jpg)

可以自己部署服务器，也可以用我们提供的[nodejs包](http://appcan-download.oss-cn-beijing.aliyuncs.com/appcan_sdk%2FAppCan-nodejs%E5%BE%AE%E4%BF%A1.zip "nodejs包")nodejs包，安装nodejs，也可以参考nodejs官方文档,按照完成后输入node –version;查看nodejs是否安装成功
![](http://newdocx.appcan.cn/docximg/151622m2015s2l23y.jpg)

部署我们提供的nodejs包，可以在index.js中修改端口号，你的webapp应该放在public文件下，该目录默认为静态文件目录，你也可以在index.js中修改
![](http://newdocx.appcan.cn/docximg/151646f2015n2k23n.png)

把该包传到服务器上然后，切换到相对应目录用node index.js来启动服务
![](http://newdocx.appcan.cn/docximg/151717g2015q2o23b.jpg)

我们就可以在手机上访问我们的web app网站了地址为：````http://ip:port/loader.html````
如果需要配置默认也面可以设置index.js
app.use(express.static(path.join(__dirname,'public'),{index:'loader.html'}));

如果我们想生成微信的app，调用微信的接口，我们需要修改一下配置文件，来启动签名服务。打开config目录下面的config.js文件
![](http://newdocx.appcan.cn/docximg/151746c2015c2s23e.png)

在微信的公众号管理后台中找到这些参数，参考：
[http://mp.weixin.qq.com/wiki/17/2d4265491f12608cd170a95559800f2d.html](http://mp.weixin.qq.com/wiki/17/2d4265491f12608cd170a95559800f2d.html)
[http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html)
![](http://newdocx.appcan.cn/docximg/151818y2015s2b23i.png)

配置完成后重写启动node服务器后，可以打开默认的签名服务接口
![](http://newdocx.appcan.cn/docximg/151923d2015b2c23m.png)

然后修改loader.html中setWeiXinConfig(url);url为该完整路径包括后面的要签名的url
在微信中打开然后所有的接口都可用了，demo效果,[demo下载](http://appcan-download.oss-cn-beijing.aliyuncs.com/appcan_sdk%2F%E5%BE%AE%E4%BF%A1%E5%A4%9A%E5%85%A5%E5%8F%A3demo.zip)
![](http://newdocx.appcan.cn/docximg/151959f2015h2m23s.png)

####3、常见问题及解决方法
1）、名称冲突：如果你修改了一个元素属性或者一个元素的样式不起作用时，你可以考虑一下去检查是不是元素命名冲突了，因为我们要把所有的popover合并到一个页面中所以会有冲突问题。
2）、css样式覆盖：如果你加载一个页面后原始页面的其他样式乱了，你可以考虑一下新页面中的样式是否把原有样式覆盖了，因为我们要把所有的popover合并到一个页面中所以会有冲突问题。
3）、css样式不起作用：如果你打开一个新的popover页面，引用的css文件中修改样式不起作用，可以考虑这个问题，同一个样式在同一个win中只会加载一次，后续的不会加载。
4）、js冲突问题：如果你新打开一个浮动窗口，然后关闭了，以前写的某个方法原本好的现在报错了，可以考虑一下这个问题，因为我们要把所有的popover合并到一个页面中所以会有冲突问题。
5）、js判断问题：如果你新打开一个浮动窗口，执行一个判断某一个变量是否存在，或者不是按照正确的方式，可以考虑一下这个问题，因为我们要把所有的popover合并到一个页面中所以会有冲突问题，所以后面执行后会修改已存在的变量。
6）、body、html样式问题：如果你在body、html上面加了一些样式，在web app中可能不显示，因为我们默认会把所有的body、html、head等元素删掉。
7）、白色popover问题：由于popover会相互覆盖，web app默认会把所有的popover设置成白色，所有如果遇到这些问题的话可能是popover的问题。
8）、height设置相对值不起作用：因为我们会在所有的popover上面加上IScroll保证滚动效果，会在外部加一层，会根据实际内容来算滚动高度，所以不会起作用，可以设置固定高度解决这个问题。
9）、返回按钮：因为我们默认会加上一个#index来打开新页面，如果回退到首页的话，会再重新刷新页面，因为我们的首页是一个空白页面，来管理整个窗口。
10）、修改页面高度多出内容会覆盖：因为我们用的是IScroll加载页面，如果内容修改需要重新刷新页面保证页面滚动，请调用refreshBounce（）来保证页面效果。
11）、页面展示内容覆盖：可以考虑内容是否是异步加载的，因为我们是直接取现有的高度如果你异步加载某些内容的话重新修改高度可能会把原来的已经算好的popover覆盖掉。
12）、页面不能滑动：如果你在某一个元素上面绑定了事件，同事阻止了事件的传播这一块可能造成IScroll接受不到事件导致页面不能滑动。
13）、功能不能用：请检查是否用到了没有封装的接口，目前我们只对uexWindow做了封装，如果是微信内运行的话还有一些微信的插件可以支持，另外如果取数据的话可以把appcan.request.ajax 改为Zepto.ajax,同时保证参数问题，因为Zepto传文件会有问题，建议复用函数，这些多多少少还是有一点不同的，getJSON，get，post这些方法完全可以使用。