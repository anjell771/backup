

<h5 id="h5-1"><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 1、ide 打包时 进度条显示完，没有弹出生成的应用文件存放目录怎么办？</h5>

如图：
![我的头像](http://newdocx.appcan.cn/docximg/154213w2015h1k26h.jpg)

![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png)  **解决方式**
如图显示，自己检查一下，这个是你的源码文件存在中文字符的文件，appcan打包服务器不认可中文字符文件，重点是查看error报错内容

<h5 id="h5-2"><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 2、调试中心按照文档步骤操作，没有显示效果？</h5>

![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
（注意：真机调试必要条件：设备与pc必须在相同网段）装在pc端的IDE与要调试的设备链接同一个网段，在同一个wifi或者公司内网环境。判断方法：在设备浏览器里输入“调试服务器的ip：30060”如192.168.1.213：30060看一下访问的页面是否是weinre server home的显示页面
<h5 id="h5-3"><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 3、 IDE生成的ipa包安装失败</h5>

![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
IDE打包环境只是一个测试环境，正式发布打包还需到云端打包，IDE生成的ipa包是越狱包，只能在越狱机安装，

<h5 id="h5-4"><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 4、 IDE打包提示“没有设定合法的应用key”</h5>

![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
关闭config.xml文件，重新打开config.xml文件，配置一下key即可

<h5 id="h5-5"><a name="h5-4" class="reference-link"></a><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 5、 IDE打包报错信息汇总”</h5>

如下：
````
cmd.exe /C set JAVA_HOME=D:\AppCan\AppCanStudioPersonal\AppCan-IDE\jre&&set PATH=D:\AppCan\AppCanStudioPersonal\AppCan-IDE\jre\bin;&&“D:\AppCan\AppCanStudioPersonal\HDK\tools\utility_zy.exe“ w=“E:\code\android\wuye\phone“ o=“D:/AppCan/AppCanStudioPersonal/Mobile-Applications\wanjia.apk“ r=“D:\AppCan\AppCanStudioPersonal\HDK\tools\pic“ id=0000014d-650a-efb3-0000-014d650aefb3 n=“wanjia“ p=android color=#ffffff appkey=102203322-1021-2039-2000019221 wv=1.02orientation=UIInterfaceOrientationPortrait fullscreen=true plugin=uexDataBaseMgr,uexDevice,uexFileMgr,uexLog,uexXmlHttpMgr,uexLocation
Java 运行环境未找到。
````
````
3.2.0没有自动选择插件那个checkbox，打包的时候总是报错
cmd.exe /C set JAVA_HOME=E:\AppCan\AppCanStudioPersonal\AppCan-IDE\jre&&set PATH=E:\AppCan\AppCanStudioPersonal\AppCan-IDE\jre\bin;&&“E:\AppCan\AppCanStudioPersonal\HDK\tools\utility_zy.exe“ w=“E:\AppCan\AppCanStudioPersonal\AppCan-IDE\plugins\com.appcan.ide.eclipse.hdt.player_1.0.0.201503161536\AppCanPlayer“ o=“E:/AppCan/AppCanStudioPersonal/Mobile-Applications\AppCan调试中心.apk“ r=“E:\AppCan\AppCanStudioPersonal\HDK\tools\pic“ id=001 n=“AppCan调试中心“ p=android color=#ffffff appkey=AppCan wv=1.02orientation=UIInterfaceOrientationPortrait fullscreen=false plugin=uexActionSheet,uexAliPay,uexAudio,uexBrokenLine,uexButton,uexCall,uexCamera,uexClipboard,uexContact,uexControl,uexCoverFlow2,uexCreditCardRec,uexDataBaseMgr,uexDevice,uexDocumentReader,uexDownloaderMgr,uexEditDialog,uexEmail,uexFileMgr,uexHexagonal,uexImageBrowser,uexIndexBar,uexListView,uexLocalNotification,uexLocation,uexLog,uexMMS,uexPDFReader,uexPie,uexPieChart,uexQQ,uexSMS,uexScanner,uexSensor,uexSina,uexSlidePager,uexSocketMgr,uexTent,uexTimeMachine,uexUploaderMgr,uexVideo,uexWeiXin,uexWheel,uexXmlHttpMgr,uexZip
Error occurred during initialization of VM
Unable to load native library: Can`t load AMD 64-bit .dll on a IA 32-bit platform
````
![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
`Can't load AMD 64-bit .dll on a IA 32-bit platform` 32位的系统加载了64位的.dll，重新检查你配置的JDK环境.

<h5 id="h5-6"><a name="h5-6" class="reference-link"></a><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 6、 IDE生成Appcan调试中心的时候报错</h5>

如下：
````
cmd.exe /C set JAVA_HOME=C:\AppCan\AppCanStudioPersonalV3.2\AppCan-IDE\jre&&set PATH=C:\AppCan\AppCanStudioPersonalV3.2\AppCan-IDE\jre\bin;&&"C:\AppCan\AppCanStudioPersonalV3.2\HDK\tools\utility_zy.exe" w="C:\AppCan\AppCanStudioPersonalV3.2\AppCan-IDE\plugins\com.appcan.ide.eclipse.hdt.player_1.0.0.201503161536\AppCanPlayer" o="C:/AppCan/AppCanStudioPersonalV3.2/Mobile-Applications\Appcan.apk" r="C:\AppCan\AppCanStudioPersonalV3.2\HDK\tools\pic" id=001 n="Appcan" p=android color=#ffffff appkey=AppCan wv=1.02 orientation=UIInterfaceOrientationPortrait fullscreen=false plugin=uexActionSheet,uexAliPay,uexAudio,uexBrokenLine,uexButton,uexCall,uexCamera,uexClipboard,uexContact,uexControl,uexCoverFlow2,uexCreditCardRec,uexDataBaseMgr,uexDevice,uexDocumentReader,uexDownloaderMgr,uexEditDialog,uexEmail,uexFileMgr,uexHexagonal,uexImageBrowser,uexIndexBar,uexListView,uexLocalNotification,uexLocation,uexLog,uexMMS,uexPDFReader,uexPie,uexPieChart,uexQQ,uexSMS,uexScanner,uexSensor,uexSina,uexSlidePager,uexSocketMgr,uexTent,uexTimeMachine,uexUploaderMgr,uexVideo,uexWeiXin,uexWheel,uexXmlHttpMgr,uexZip
'"C:\AppCan\AppCanStudioPersonalV3.2\HDK\tools\utility_zy.exe"' 不是内部或外部命令，也不是可运行的程序
或批处理文件。
````
![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
检查一下C:\AppCan\AppCanStudioPersonalV3.2\HDK\tools\utility_zy.exe是否存在. 可能在安装IED时,被你装的杀毒软件隔离或者 删掉了. 看看是否能恢复,如果不能,你就卸载重装一遍,注意,不要再把文件删掉.
<h5 id="h5-7"><img src="http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Ff.png" alt="问"> 7、IDE中本地调试web/微信 App服务勾选在一定端输入`ip:端口号3005`无效</h5>

![答](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fq.png) **解决方式**
首先确保移动设备与pc保持在相同网段，其次检查下勾选config.xml文件的web/微信 App服务之后有没有自动生成一个loader.html文件，上次之后再移动端重新输入`ip：端口号`调试
![ ](http://newdocx.appcan.cn/docximg/155707z2015m6g8g.jpg) 