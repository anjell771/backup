
  AppCan IDE是基于Eclipse定制的移动集成开发环境，专为无Native开发经验的HTML开发人员设计。
 AppCan IDE帮助HTML开发人员在无需任何原生环境辅助下即可完成高体验效果应用的开发、调试、跟踪和模拟，并可借助内嵌的应用打包功能，创建可直接安装到手机的本地应用安装包以便后续测试应用。
   
### 跨平台支持
  AppCan IDE可以用于支持iOS、Android平台手机和平板的高体验Hybrid应用的开发。通过AppCan Hybrid技术，HTML开发人员遵循基于标准CSS技术的AppCan 移动开发UI参考框架，即可完成一次开发，多平台适配，在各种分辨率的移动终端上保持相同的体验。AppCan UI框架提供了极高的适配性和自主性，开发人员可以没有束缚地根据需求、UI设计完成应用界面及逻辑的开 发。
  
### HTML5支持
  AppCan IDE采用国际通用的HTML语言作为跨平台支撑语言，同时借助于AppCan Hybrid技术以终端内嵌浏览器为核心的设计理念，使开发人员可以直接采用HTML5技术完成应用功能的开发。基于业界公认的HTML5的强大能力和广泛的开发用户群体，开发人员不需要重新学习私有标准，即可完成复杂功能的实现。
 
### UI模版支持
  AppCan IDE内嵌了电商、新闻等多套业界经典应用模板，开发人员可以基于模板快速构建应用框架，同时IDE还内嵌了登录、注册、个人信息、购物车等等超过百款移动经典窗口布局模板，并以界面向导方式交付，有效帮助开发者快速完成应用的界面和功能拼装。
 
### 本地打包支持
   AppCan IDE内嵌开发版应用打包服务，开发人员可以在个人PC机上完成开发版本应用安装包的生成，并可在手机中安装验证应用的实现效果与问题解决情况。开发人员可以在本地配置应用启动界面、图标，还可以动态选择应用所用的公共插件和自定义插件。打包服务会自动聚合各插件库、引擎和应用HTML代码。通过生成的安装包，可以直接验证插件的功能，便于插件开发人员与HTML开发人员进行联调，同时还可验证应用图标、启动图片等资源的实际展示效果。
 
### 本地模拟调试
  AppCan IDE提供基于Chrome内核的模拟器，可以在PC上完成移动应用的界面模拟、通讯模拟、设备模拟。开发者可以在模拟器中动态跟踪和调试代码，变更显示效果，作断点调试。
 
###  真机同步调试
  AppCan IDE为开发者提供了Android和iOS平台的真机同步调试功能，不仅能快速方便调试JavaScript、检查HTML页面DOM结构、实时同步更新元素CSS样式，还能跟踪分析页面资源加载性能等问题，帮助开发者高效、便捷的调试应用。
  
### IDE新版特色
  AppCan IDE 3.1版本更加人性化，提供应用向导和界面向导，内置多种主题方案、UI控件及数百种界面模板，支持项目同步，支持本地应用打包、本地模拟调试和真机实时同步调试，引擎插件再次升级适配iOS8,代码提示无忧编程，助开发者快速上手，高效创建专业应用。
 
###  AppCan IDE 3.2新版特色：
 
1）、新增边改边看实时预览功能，支持代码调试、插件模拟
2）、新增Web/微信 App打包功能，可将移动应用快速转换为移动网站和微信网站
3）、优化版本更新，提示新版本更新日志
4）、引擎、插件强大升级
5）、丰富稳定的UI组件，海量的行业页面模版
6）、项目云端同步，多人协同开发
7）、真机实时同步调试
8）、优化代码提示

###   IDE八大改进
IDE新版上线了，在IDE新版本上开发者会发现几大改变，这些改变能让开发者更快速、 高效的开发更加稳定的项目。

####   1）appcan.ready替换window.uexOnload

在新版本中使用appcan.ready替换window.uexOnload,并且在同一html页面中可以多次调用appcan.ready。新代码如下：
```
appcan.ready(function() {
            var titHeight = $('#header').offset().height;
            appcan.frame.open("content", "index_content.html", 0, titHeight);
            window.onorientationchange = window.onresize = function() {
                appcan.frame.reisze("content", 0, titHeight);
            }
});
```
####   2）重新定义页面弹动刷新功能
在新版本中，重新定义了页面的弹动刷新方法。将多个零散的方法进行封装统一调用，简化插件调用步骤，更容易实现弹动刷新功能。原来我们调用此功能的代码要调用以下方法：

uexWindow.setBounce(flag)；
uexWindow.notifyBounceEvent(type, status)；
uexWindow.showBounceView(type, color, flag)；
uexWindow.resetBounceView(type)；
uexWindow.setBounceParams(type, json)；
uexWindow.hiddenBounceView(type)；
uexWindow.onBounceStateChange
现在，我们只需按如下代码调用即可：
```
appcan.frame.setBounce([0,1], function(type) {
                $("#pullstatus"+type).html(!type?"开始下拉":"开始上拖");
            }, function(type) {
                $("#pullstatus"+type).html(!type?"下拉超过临界点,产生事件了！":"超过临界点,产生事件了！");
            }, function(type) {
                $("#pullstatus"+type).html("松手了,产生事件了,开始更新数据！");
                setTimeout(function() {
                    appcan.frame.resetBounce(type);
                    $("#pullstatus"+type).html("");
                    demo.add(updateData,type);
                }, 1000);
});
```

####   3）修改UI控件实现方式
在新版本中，重新定义UI控件的实现方式，减少代码的编写量，更加快速便捷的实现功能及界面展现。如listview控件，在之前的版本中我们实现列表，在html中直接加入列表的具体代码，数据拼装及显示需要进行代码的具体编写控制；而在新版本中我们通过js控制只需填入关键数据即可实现模版数据的拼装及显示。如下面这段js：

```
var updateData = [{
            title : "飞行模式",
            icon : "../css/res/appcan_s.png",
            "switch":{
                mini:true,
                value:false
            }
        }, {
            title : "蓝牙",
            subTitle:"打开",
            icon : "../css/res/appcan_s.png"
        }];
        var lv1 = appcan.listview({
            selector : "#listview",
            type : "thinLine",
            hasIcon : false,
            hasAngle : true,
            hasSubTitle : false,
            multiLine : 1,
            hasControl : true,
            align : 'left'
        });
        lv1.set(updateData);
```
上面这段js代码是直接生成，我们只需将updateData里的数据换成我们要显示的数据即可。

####   4）集成backbonejs、zeptojs和underscorejs进而与jQuery等写法兼容
在原来的版本中，我们使用$$通过id获取元素的dom，除此之外未提供任何快捷方法，现在我们可以直接使用$加元素选择器的方式获取我们想要的dom，并且对dom进行操作了。通过这种方式编写，让习惯了使用第三方框架的开发者更加快捷高速的进行编码。如$(“#id”).removeClass、$(body)等。

####   5）推出js sdk对底层的接口进行更高层的封装，统一规范接口调用体系。
使用IDE3.1版本，开发者会发现在新建的项目里的js文件换了，这里appcan根据自己的需求封装的一个开发库- AppCan javascript sdk，对底层的接口进行更高层的封装，能让开发者更快速、 高效的开发更加稳定的项目，该库依赖backbonejs、zeptojs、underscorejs默认打包在基础库中，开发者不需要进行额外的引用，另外在该库的基础上提供了丰富的插件，能让开发者更高效的开发app。
这个封装的库里分为很多模块，如文件模块file，网络请求request等。现在我们使用uexWindow的一些方法，我们可以在appcan.window中找到，浮动窗口的相关方法在appcan.frame中找到。

 #### 6）增加调试中心功能
 AppCan调试中心是AppCan IDE为开发者提供的一款可真机同步调试的门户应用，在同一wifi环境下，它与pc端工作空间相关连，摆脱数据线，无需二次打包，就可实时测试修改应用。此外AppCan IDE3.1为开发者提供了Android和iOS平台真机同步调试功能，只需配置当前应用的config文件，真机上的应用就可实现与PC端的实时同步调试功能，帮助开发者高效率、便捷的调试应用。

 #### 7）新增配色主题选择功能
针对旧版本自由调色导致配色出现不和谐问题，新版新建项目即将完成时新增配色主题选择功能，在不同的主题下项目的按钮、边框、背景等配色进行统一更改，进而免除了开发者对项目的配色烦恼。目前的主题色为中国红、蜜桃粉、青草绿、天际蓝、子夜黑五种主题色。

####  8）IOS7及以上系统状态栏自动设置
新版本针对IOS7及以上系统状态栏做了自动设置，只要是新建的项目，此功能代码已加入到js及css代码中，开发者不需要为这个问题单独进行设置。