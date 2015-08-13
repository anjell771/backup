[TOC]
###  1.开发环境搭建

  Android的开发环境搭建主要包括JDK、Eclipse、Android SDK的安装。

  您也可以直接安装好JDK后，去Android官网下载ADT套装 推荐下载地址：(http://developer.android.com/tools/index.html) ，解压缩即可使用。

  整个安装过程较为简单，下面主要验证JDK和Android SDK是否安装成功的问题。

  [AppCan Android插件资源环境下载](http://download.appcan.cn/appcan_sdk/Android.rar)



#### 1.1.JDK安装验证

  安装完成之后，可以在检查JDK是否安装成功。打开cmd窗口，输入java –version 查看JDK的版本信息。出现类似下面的画面表示安装成功了：
![](http://newdocx.appcan.cn/docximg/160544v2014z8p26y.png)


#### 1.2.Android SDK安装验证

  进入cmd命令窗口，检查SDK是不是安装成功。 运行 android –h 如果有类似以下的输出，表明安装成功：

![](http://newdocx.appcan.cn/docximg/160605h2014z8d26d.png)

### 2.扩展插件的开发
 
 #### 2.1.开发流程
**2.1.1.插件开发基本流程**

 2.1.1.1.插件开发基础工程搭建


  将AppcanPluginDemo3.0 导入eclipse,此工程为插件开发基础工程,工程内res及assets文件夹含有插件开发的必要文件,开发者不要随意删除。

![](http://newdocx.appcan.cn/docximg/145022u2014g10s28l.png)

2.1.1.2.将代码集成到AppCan基础开发工程


2.1.1.2.1.插件入口类编写

  编写插件代码时，应当有至少一个入口类，需要说明的是，此类须继承基础类EUExBase类，并实现或重写父类的相关方法，随后我们就可以按照自己的功能需求编写代码了。

  例如在入口类uexDemo中，编写了一个打开activity的方法，实现打开编写好的HelloAppCanNative(请读者自行完成，此处省略HelloAppCanNative编写过程)。
![](http://newdocx.appcan.cn/docximg/160645c2014g8m26e.png)


 2.1.1.2.2.插件配置文件编写

  入口类编写好后，想在网页端调用入口类的方法，这就需要配置文件来处理。

  注意在工程的res/xml文件夹下，有一个plugin.xml文件，此文件就是链接插件与网页的桥梁。
![](http://newdocx.appcan.cn/docximg/160703w2014s8y26g.png)
  在plugin.xml文件中，最外部的标签统一````<uexplugins>````,接下来配置````<plugin>````标签,此标签包含两个属性，className为入口类的包名加类名，uexName是给入口类起的别名。最后需要配置子标签````<method>````，子标签的name属性即为入口类内已经编写好的方法。

  如有多个入口类,继续添加````<plugin>````标签即可。



 2.1.1.2.3.Html页面调用插件配置

  入口类和插件配置文件都配置完毕,现在需要在html页面调用入口类的方法。

  注意到在工程assets/widget/下,有index.html文件,此网页即为入口类的调用入口。

  在网页内编写代码，实现调用入口类uexDemo内打开activity的方法：
![](http://newdocx.appcan.cn/docximg/160726r2014r8l26m.png)
  其中onclick的属性值为:入口类的别名.方法名()。



2.1.1.2.4.AndroidManifest.xml配置

  打开AppcanPluginDemo3.0 工程，开发者不要改动AndroidManifest的application节点下的所有属性(如果改动，只有本地测试有效，插件打包后application节点下的任何更改不起作用)；

  插件的入口activity也不要改动，程序打开后会默认进入此activity，弹出assets/widget/index.html页面。
![](http://newdocx.appcan.cn/docximg/160744d2014g8w26d.png)


2.1.1.3.测试插件

  在工程上右键,选择“run as”--->“Android Applicition”--->“运行程序”,即可跳转到如下界面;点击按钮,即可实现调用入口类的相应方法。
![](http://newdocx.appcan.cn/docximg/160800k2014y8c26l.png)


** 2.1.2.生成插件包**

  插件是为了实现跨平台统一性和实现一些网页中不能实现的功能，插件最后的展现形式是.zip压缩包，插件又分为两种：一种是用于AppCan SDK移动应用开发系统上，另一种是用于AppCan 3.0 IDE上。

  1）如何生成用于 AppCan SDK移动应用开发系统上的插件包以及所需文件，请参考下边“如何生成 AppCan SDK移动应用开发系统插件包”。

  2）如何用于AppCan 3.0 IDE上的插件包以及所需文件，请参考下边“如何生成AppCan 3.0 IDE插件包”。



#### 2.2.最终插件包目录结构命名规范

  插件文件的命名可任意，但在AppCan中有统一的命名规范，为了保持一致扩展插件的开发也要符合命名规范。
![](http://newdocx.appcan.cn/docximg/182810b2015s3r14v.jpg)

****第2层目录文件夹的命名规则取自info.xml的uexname****
![](http://newdocx.appcan.cn/docximg/183014p2015n3z14t.png)
**2.2.1.plugin.xml中类及方法的命名**

  plugin.xml 文件位于res目录下的xml目录中，是配置自定义native Plugin调用对象的xml文件，如果需要自定义对象和开发原生插件，必须在此文件中配置自定义js对象名和java类的包名类名。下面以AppcanPluginDemo3.0 插件为例：
![](http://newdocx.appcan.cn/docximg/160822f2014y8f26g.png)
 >**** uexName****：为封装的js对象的名称，以uex前缀开头，即uex+对象英文名称；

  >****className****：与js对象映射的java对象的路径包名及类名，建议命名为EUEx前缀+名称；

 > ****method****：插件对象中的方法名称，依旧符合驼峰命名法，回调网页的函数不需要写入到此文件中，但是应写到插件的API文档中。



** 2.2.2.类的命名**

  插件入口类的命名前缀为EUEx，即类的命名规范为EUEx+对象英文名称，例如EUExDemo，又例如我们已经封装的下载管理插件EUExDownloaderMgr等。当然这个命名规范不是必须的，但是必须保证插件入口类的类名和plugin.xml中的类名一致即可。


**2.2.3.方法的命名**

  方法名符合驼峰命名法，例如下载接插件中的创建下载对象“createDownloader”，和下载“download”。值得注意的是，这里的方法名要与plugin.xml中的相应类下的method name保持一致，否则会调用失败。



**2.2.4.jar包的命名**

  扩展插件最终是以“.jar”的形式提交到服务器，也要符合我们的命名规范，即plugin_+插件名称。其中插件名称要和plugin.xml中的uexName一致。例如plugin_uexDemo.jar，和下载管理插件plugin_DownloaderMgr.jar等。



** 2.2.5.资源文件的命名**

  命名规则为plugin_+plugin对象名_+其他信息，例如plugin_uexdemo_xxx.png、plugin_uexdemo_yyy.xml、<string name=" plugin_uexdemo_zzz ">等等。

#### 2.3.插件组成

插件文件的命名可任意，但在AppCan中有统一的命名规范，为了保持一致扩展插件的开发也要符合命名规范。

**2.3.1. AppCan SDK移动应用开发系统插件包组成**

插件是以.zip文件的形式存在的，解压之后如下：
![](http://newdocx.appcan.cn/docximg/160842k2014f8n26m.png)
  AppcanPluginDemo3.0 插件包含的文件有plugin.xml、info.xml（AppCan3.0新添加文件）、AndroidManifest.xml文件、jar文件、res文件夹（如果插件使用资源文件就需要有个文件夹，没有就不需要）。

 2.3.1.1.Plugin.xml文件

将plugin.xml 文件添加到res目录下的xml目录中，按照命名规范填写插件中用到的类、方法等。例如AppcanPluginDemo3.0 工程中，用到uexDemo对象名，startActivityForResult方法等，如图：
![](http://newdocx.appcan.cn/docximg/160859x2014x8i26d.png)


2.3.1.2.info.xml文件

此文件是AppCan3.0新引入的文件，主要用于说明插件版本信息和更新内容等。Info.xml文件的内容如下：
![](http://newdocx.appcan.cn/docximg/160915g2014b8o26p.png)

 >****uexName****：代表插件名字。

>  ****version****：代表当前插件的版本号，以后通过info.xml文件也可以知道当前插件的版本信息。

>  ****build****：代表当前插件的小版本，内部使用。

 > ****info****：代表当前插件版本修改信息，以后通过info.xml文件也可以知道当前插件此版本修改信息。

  在AppCan3.0中此文件是新添加的并且必须要有的，请开发人员注意。



2.3.1.3.AndroidManifest.xml

  配置本插件中用到的activity、service、receiver权限，以及应用的属性，例如横竖屏启动等等。可参考AppcanPluginDemo3.0 工程中的AndroidManifest.xml文件。



2.3.1.4.jar文件夹

  此中存放插件jar包，这是插件包上传的必备文件。



**2.3.2.AppCan 3.0 IDE插件包组成**

2.3.2.1.plugin.xml文件

同AppCan SDK移动应用开发系统插件中的plugin.xml。



 2.3.2.2.info.xml文件

同AppCan SDK移动应用开发系统插件中的info.xml。



2.3.2.3.AndroidManifest.xml
同AppCan SDK移动应用开发系统插件中的AndroidManifest.xml



2.3.2.4.jar文件夹
同AppCan SDK移动应用开发系统插件中的jar文件夹。


2.3.2.5.dex文件夹
此文件夹存放在AppCan 3.0 IDE 中可用的jar包，这是AppCan 3.0 IDE生成安装包的必备文件（````请开发人员注意````）。

如何生成AppCan 3.0 IDE 可用的jar包，请参考下面“生成可用于AppCan 3.0 IDE的jar包”。



#### 2.4.插件代码详细介绍

编写插件代码时，应当有至少一个入口类，提供给前端使用，此类须继承plugin的基础类EUExBase类，然后实现或重写相关函数，并添加自定义的接口方法与plugin.xml中的method对应。开发插件中可能遇到的常见问题，请查看下文中的插件开发中常见问题部分。



** 2.4.1.编写基础类**

代码中继承的接口主要包括以下3个：

 **** EUExBase.java：****

封装了JS调用native

以及native回调JS的桥接函数的父类，任何Native扩展插件的对象均需要继承此类；

  ****EUExUtil.java：****

  提供动态获取本应用资源id等功能的工具类。

  注意：AppCan中的所有资源文件，包括字符串资源等，都必须使用此工具类当中的相关函数动态获取其资源ID，而不能直接使用R文件引用！具体使用方法请参考下文中“如何调用res中的资源”。

 **** EUExCallback.java：****

  与plugin的callback相关的一些常量，不再一一列举，可自行查看。



**2.4.2.定义与js对象映射的java类**

  新建java类UexDemo.java并继承自EUExBase。如图：
![](http://newdocx.appcan.cn/docximg/160939o2014f8k26z.png)
  工程中其余部分按照插件的开发需求编写，但要注意命名规范。

  其中：所有接口函数的参数均为1个string数组。此数组的长度即为js传过来的参数个数，此数组的index与js中参数的index相对应。

  例如，在js中有类似调用：uexDemo.showInputDialog (p1，p2，p3，p4)

  那么，当它映射到UexDemo.java的：public void showInputDialog (String[] parm)函数中时，parm的长度将为4，可通过parm[0]取得p1，parm[1]取得p2，parm[2]取得p3，parm[3]取得p4，以此类推。如图所示：
![](http://newdocx.appcan.cn/docximg/161009s2014o8r26b.png)
  继承EUExBase类必须实现clean方法, 是平台封装的调用方法，把一些与当前网页有关的内存等等在切换网页的时候释放掉（请参考AppcanPluginDemo3.0 工程）。

  注意，clean(String[] params) 方法当切换窗口时会自动调用，因此如果想保持某些资源在不同窗口中使用，则不应当再此方法中回收资源。



**2.4.3.向网页回调数据**

  方法主要分为两种：

  ****标准回调方式：****

  AppCan平台的Native扩展插件中，推荐使用的回调规则是uexDemo.cbMethodName(opId,dataType,data)，其中opId代表操作码区分操作，dataType用来表示data的类型，data是回调数据。这种回调方式可以使用平台提供的封装方法jsCallback来实现。

  下面是一个返回json数据的例子：
![](http://newdocx.appcan.cn/docximg/161032u2014c8r26d.png)
  ****自定义回调方式：****

  除了使用标准回调方式，还可以使用自定义的回调方式，返回js的参数个数和类型可以根据需要自定义。这种回调方式应使用平台提供的封装方法onCallback来实现。

  下面是一个自定义回调的例子：
![](http://newdocx.appcan.cn/docximg/161054e2014u8m26t.png)
  其中SCRIPT_HEADER是EUExBase中的常量，继承后可以直接使用，方便拼接js字符串，也可以自己写上javascript:代替。后面的ON_FUNCTION_MAP_DRAG为预先自定义好的回调方法名，形式与上面的标准回调方式中相同，具体参照命名规范说明。



#### 2.5.如何生成AppCan SDK移动应用开发系统插件包

  AppCan SDK移动应用开发系统插件包主要组成部分：

  ****JAR文件夹:****

  工程src下所有的类打出来的包文件存放在此目录下；

  ****res文件夹：****

  将插件工程res文件夹下自己使用到的图片，xml文件等（AppcanPluginDemo3.0 工程自带的资源文件除外）复制出来，放在res文件夹下；

 **** AndroidManifest.xml文件：****

  将插件工程的AndroidManifest.xml文件复制出来即可，具体见下文“AndroidManifest.xml文件配置”；

 **** Plugin.xml文件：****

  将插件工程res/xml下的plugin.xm复制出来即可，具体修改见上文“plugin.xml中类及方法的命名”的介绍；

  ****info.xml文件：****

  此文件是AppCan3.0新引入的文件，主要用于说明插件版本信息和更新内容等。

  一个带有资源文件的原生插件包目录结构一般类似于下图：
![](http://newdocx.appcan.cn/docximg/161125f2014q8i26w.png)
  > 注意事项：

> （1）、其中 so 文件夹和res文件夹为可选项，如果插件里引用的有自己开发的ndk生成的so文件或者是第三方的so文件，就在插件目录结构里新建so文件夹，将so文件放到so文件夹下````（注意：该文件夹下直接放.so格式的文件，不能再嵌套任何文件夹）````，如果插件里没有引用so文件，则无需建立此文件夹。

> （2）、其中jar 文件夹用来放置自己导出的jar文件和第三方的jar文件，其中res文件夹用来放置布局和资源文件````（只放自己应用需要的，系统demo自带的不能放进去）````，内部目录结构和Android原生开发里面的res目录结构相同。AndroidManifest文件里面只需要写入自己插件里面用到代码即可，plugin里面用来注册插件接口。

> （3）、其中，jar目录用来存放你的jar文件的目录，jar文件，info.xml文件和 plugin.xml文件是在线插件zip包必须包含的，其他不带资源文件的插件可能没有res目录或者没有AndroidManifest.xml文件。

  以下为插件包中相应目录及文件的详细解释：


** 2.5.1.jar文件夹**

  此中存放插件jar包，这是插件包上传的必备文件。命名必须符合命名规则，plugin_+扩展对象名+具体的后缀，如：plugin_uexDemo.jar。

制作jar包方法：选中插件工程src下所有包和类文件，右键选择Excport--Java--JAR file,选择输出路径按照提示打包即可。


**2.5.2.plugin.xml文件配置**

  plugin.xml是上传的必备文件，内容见上文中命名规范说明。


**2.5.3.info.xml文件配置**

  info.xml是上传的必备文件。此文件是AppCan3.0新引入的文件，主要用于说明插件版本信息和更新内容等。Info.xml文件的内容如下：
![](http://newdocx.appcan.cn/docximg/161327g2014n8s26y.png)
 **** uexName：****代表插件名字。

  ****version：****代表当前插件的版本号，以后通过info.xml文件也可以知道当前插件的版本信息。

  ****build：****代表当前插件的小版本，内部使用。

  ****info：****代表当前插件版本修改信息，以后通过info.xml文件也可以知道当前插件此版本修改信息。

  AppCan 3.0中此文件是新添加的并且必须要有的，请开发人员注意。



**2.5.4.AndroidManifest.xml配置**

  AndroidManifest.xml是非必须的，用于配置本原生插件中用到的activity，service，receiver，权限等的主配置文件。只配置此plugin用到的。其结构类似于下图：
![](http://newdocx.appcan.cn/docximg/161454n2014n8g26i.png)


**2.5.5.res文件夹**

  res文件夹是非必须的，用于存放扩展插件特有的资源。此目录中的所有目录同AppcanPluginDemo3.0 工程的res目录相对应。因此提交时要将资源放到相应的文件夹下，命名应当符合上文中提到的命名规则。目录结构及命名规则示例如图：
![](http://newdocx.appcan.cn/docximg/161536r2014l8i26u.png)
![](http://newdocx.appcan.cn/docximg/161554d2014l8i26e.png)

#### 2.6.如何生成AppCan 3.0 IDE插件包

  AppCan SDK移动应用开发系统插件包主要组成部分：

  首先解压缩已有的标准插件，可以看到插件的目录结构如下图所示：
![](http://newdocx.appcan.cn/docximg/161612l2014n8p26i.png)
  其中 so 文件夹和res文件夹为可选项，如果插件里引用的有自己开发的ndk生成的so文件或者是第三方的so文件，就在插件目录结构里新建so文件夹，将so文件放到so文件夹下````（注意：该文件夹下直接放.so格式的文件，不能再嵌套任何文件夹）````，如果插件里没有引用so文件，则无需建立此文件夹。jar 文件夹用来放置自己导出的jar文件和第三方的jar文件，res文件夹用来放置布局和资源文件，内部目录结构和Android原生开发里面的res目录结构相同，AndroidManifest文件里面只需要写入自己插件里面用到代码即可，plugin里面用来注册插件接口。

  在该目录结构下新建dex文件夹，里面用来放置生成的AppCan 3.0 IDE可用的jar文件：
![](http://newdocx.appcan.cn/docximg/161632i2014g8m26d.png)
  首先打开命令提示符，转到Android SDK路径下的 sdkuild-toolsandroid-4.3这个路径，如图所示：
![](http://newdocx.appcan.cn/docximg/161653h2014n8g26x.png)
  将插件用到的所有jar文件（包括自己本地实现导出的jar文件）拷贝到该路径下，如图所示：以uexFlowDetection插件为例：
![](http://newdocx.appcan.cn/docximg/161711t2014q8d26w.png)
  该插件总共有4个jar文件，包括三个第三方的jar文件和一个本地自己导出的jar文件，编辑命令，如图所示：
![](http://newdocx.appcan.cn/docximg/161731f2014h8m26n.png)
  命令解释：dx –dex –output= 为命令头，是固定的，命令行中 plugin_uexFlowDetection_dex.jar 为要生成的字节码文件，命名格式为 plugin_uexXXX_dex.jar。后面四个参数为该插件所要用到的4个jar文件，插件用到多少个jar文件，后面跟多少个jar文件的名字。点击回车，即可生成字节码文件，生成后如图所示：
![](http://newdocx.appcan.cn/docximg/161751e2014z8m26g.png)
  上图中红框内的即为生成后的字节码文件。

  将该字节码文件拷贝到第2步创建的 dex 文件夹内，打包插件即可，到此一个AppCan SDK移动应用开发系统插件包，已经成功生成为一个可以AppCan 3.0 IDE中使用的插件包。



### 3.插件开发中常见问题

#### 3.1.如何添加一个窗口

  在AppCan平台中，为了便于管理窗口和与前端js交互，开启新的Activity时应当用主Activity转换为ActivityGroup来管理由插件开启的新Activity。示例代码如下：
![](http://newdocx.appcan.cn/docximg/161810e2014e8o26d.png)


#### 3.2.如何调用res中的资源

  在AppCan的插件开发中，不应使用应用中的R文件引用资源id，会产生问题，应当使用平台提供的EUExUtil类中的方法来通过资源名称获取对应的id。示例如下：
![](http://newdocx.appcan.cn/docximg/161828h2014q8r26r.png)
  上面是引用控件id。相应的，还有getResDrawableID，getResLayoutID等方法，它们与Android资源id类R的常用内部类一一对应，只要传入相应的资源的文件名作为参数即可（跟原生开发一样，不填写.xml .png等这种扩展名）。



#### 3.3.插件在测试中未正确运行

  > 表现：

  在eclipse中提示引擎错误，或者无法接收到原生插件传到前端的回调信息。

>   可能原因：

  1、plugin.xml文件配置错误（检查className与前端调用时使用的插件名是否一致）；

  2、info.xml文件配置错误（此文件为AppCan3.0引擎新增加的机制，必须正确配置到插件包中并填写插件相应信息，详细做法参照上文中的info.xml文件的介绍）；

  3、传递json字符串参数时应当注意，表示js字符串的引号最好用单引号，防止与json数据中的双引号产生歧义；或者最外层可以用双引号，但是内部的双引号要用 “” 转义；

  4、clean()方法为引擎再切换页面时自动调用，在其中不应处理一些页面间共享的数据的回收；

  5、若要在其他activity或者对象中向网页端回调信息，不应传递插件对象，应当定义一个回调接口并生成对象完成回调工作。



#### 3.4.插件上传后打包应用失败

 >  表现：

  在AppCan SDK移动应用开发系统中提示打包失败。

>   可能原因：

  1、插件包中的资源文件缺少；

  2、插件包结构错误（必须包含必备的目录结构，jar文件夹中要有引用的jar包和so文件，还应包含info.xml 、 plugin.xml）；

  3、资源文件存在问题（如xml格式错误、9patch图片制作出错等）。



#### 3.5.AndroidManifest常见问题

>  表现：

  在AndroidManifest下添加的属性不起作用

 >  可能原因：

  更改或添加了application节点下的相关属性(插件在最后打包时,不会提交application节点,故更改不起作用,开发者不要手动修改application节点)。
#### 3.6.如何在插件中拦截Application和Activity的系统事件
````
    public static void onApplicationCreate(Context context)
    public static void onActivityCreate(Context context)
    public static void onActivityStart(Context context)
    public static void onActivityReStart(Context context)
    public static void onActivityResume(Context context)
    public static void onActivityPause(Context context)
    public static void onActivityStop(Context context)
    public static void onActivityDestroy(Context context)
````

  使用方式：

  在入口类EUExDemo中重写上述系统事件对应的方法，
````
    public static void onApplicationCreate(Context context) {
    		Log.i("jiangpingping", "EUExLoadingView onApplicationCreate "+context);
    		if (context instanceof WidgetOneApplication) {
    			WidgetOneApplication application = (WidgetOneApplication) context;
    		}
    	}
    	
    	public static void onActivityCreate(Context context) {
    		Log.i("jiangpingping", "EUExLoadingView onActivityCreate "+context);
    		if (context instanceof EBrowserActivity) {
    			EBrowserActivity activity = (EBrowserActivity) context;
    		}
    	}

````





