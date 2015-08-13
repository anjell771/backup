[TOC]
#概述
  由于苹果的机制，在非越狱机器上安装应用必须通过官方的Appstore，开发者开发好应用后上传Appstore，也需要通过审核等环节。AppCan不 仅能实现跨平台开发，也支持上传ipa包至Appstore。本文从三个流程来介绍如何通过AppCan在线编译出ipa包并上传至苹果 Appstore。

#1．事前准备

**1.1 准备苹果帐号**
  首先您需要有一个苹果的开发者帐号，一个mac系统。如果没有帐号可以打开http://developer.apple.com/　申请加入苹果的开发者计划。如何申请网上有详细的介绍，在此不多做介绍。
如果您已经有了一个帐号，打开http://developer.apple.com/　并登录到苹果，见下图:
![](http://newdocx.appcan.cn/docximg/193744u2014d8t26c.png)

**1.2 进入证书申请界面**
  登录以后可以看到下面这个功能界面，列出了您开发需要的一些工具、支持、itunes app管理等内容。选择第二项:Certificates,ldentifiers&Profiles进入，所有证书相关的都在这里进行：
![](http://newdocx.appcan.cn/docximg/193855k2014t8r26g.png)

**1.3 申请请求文件**

**1.3.1 钥匙串程序申请请求文件**
  申请发布证书前，您需要先本地创建一个证书请求文件，截图是一个mac系统。首先打开“应用程序”->“实用工具”->“钥匙串访问（KEY CHAIN）”,在证书助理中，选择“从证书颁发机构请求证书”：
![](http://newdocx.appcan.cn/docximg/193910l2014i8c26x.png)

**1.3.2 保存请求文件设置**
  在下图所示的界面，用户电子邮件地址：填您申请帐号的电子邮件地址、常用名称（默认即可），CA空着，选择存储到磁盘，点击“继续”：
![](http://newdocx.appcan.cn/docximg/193925e2014y8o26k.png)

**1.3.3 保存请求文件名称和位置**
  选择保存的位置，比如选择桌面。下一步点击完成，您就可以看到您的桌面多了一个CertificateSigningRequest.certSigningRequest的证书请求文件。此文件申请推送证书时需要用到，请注意保存。
![](http://newdocx.appcan.cn/docximg/193940g2014y8x26t.png)

#2．申请iOS发布证书

**2.1 进入申请页面**
  继续登录到您的Member Center,选择左边的certificates项，点击All。
![](http://newdocx.appcan.cn/docximg/194001f2014g8d26v.png)

**2.2 选择申请证书类型**
  点击加号申请新证书，AppCan云端打包需要上传的是发布证书，在这里我们跳过Development开发证书，选择Production发布证书，点击In-House and Ad Hoc进入下一步。
![](http://newdocx.appcan.cn/docximg/194017b2014u8y26c.png)

**2.3 申请注意事项**
  进入Request,点击continue。
![](http://newdocx.appcan.cn/docximg/194030g2014n8s26b.png)

**2.4 添加证书请求文件**
  进入下一步Generate,点击下面的'Choose File'，选择本地创建的证书请求文件,点击Generate。
  
![](http://docx.appcan.cn/guides/ios/ios_09.png)  
 

**2.5 下载发布证书**
  现在您有一个证书可以下载了，如下图。（不能下载请刷新页面）
  ![](http://docx.appcan.cn/guides/ios/ios_10.png) 
 

#3．申请iOS应用appid

**3.1 进入申请界面**
  在下图的左边选择 App IDs，点击右上角加号按钮，开始申请一个新的AppId。对于要发布到Appstore上的程序，都有一个唯一的AppId。
  下面会列出您当前所有的AppId：
![](http://newdocx.appcan.cn/docximg/195250a2014t8d26g.png)

**3.2 填写appid标签**
  App ID Description，用来描述您的appid。（注意，必须输入英文）
![](http://newdocx.appcan.cn/docximg/195211h2014h8c26d.png)

**3.3 生成appid**
  输 入Bundle ID(App ID Suffix)：这是您appid的后缀，这个需要仔细命名，因为这个内容和您的程序直接相关，后面很多地方要用到，最好是 com.yourcompany.yourappname的格式。当然对于没有公司名的个人开发者，第二项可以用您自己的英文名字或者拼音。
AppCan.cn在线ipa包编译时需要填写的iapp IDs就是您在此输入的内容：
![](http://newdocx.appcan.cn/docximg/195140f2014d8w26f.png)

**3.4 查看生成appid**
  下图可以看见已经生成的appid。想要支持推送服务和iCould等也可以在这儿配置：
![](http://newdocx.appcan.cn/docximg/195127n2014h8c26f.png)

#4．申请iOS应用推送证书

**4.1 进入申请界面**
  在App IDs选项下，选择已经创建好的App ID，点击下方的Edit按钮。（注意，如果不要推送功能请跳过这一步）
![](http://newdocx.appcan.cn/docximg/195034v2014g8q26g.png)

**4.2 开始申请**
  输入Name，点击iCloud图标右侧的单选按钮，添加云功能。点击Push Notificotions图标右侧单选按钮，申请发布版的推送功能，点击Production SSL Certificate下方的 Create Certificate按钮。
![](http://newdocx.appcan.cn/docximg/195020n2014k8g26t.png)
![](http://newdocx.appcan.cn/docximg/194859f2014w8s26b.png)

**4.3 申请注意事项**
  依照提示点击Continue按钮。
![](http://newdocx.appcan.cn/docximg/194831e2014s8x26g.png)

**4.4 添加请求文件**
  点击Choose File按钮，选择本地请求文件，点击Generate完成创建推送证书，进行下一步：
![](http://newdocx.appcan.cn/docximg/194748g2014h8d26s.png)

**4.5 下载推送证书**
  点击Download按钮，下载生成的推送证书。（注意，证书为.cer扩展名）
![](http://newdocx.appcan.cn/docximg/194719s2014d8w26c.png)

#5．申请iOS应用的Provisioning Profiles文件

**5.1 进入申请界面**
  在下图左边选择provisioningProfiles下的All选项，点击加号按钮，申请Provisioning Profiles文件。
![](http://newdocx.appcan.cn/docximg/194701k2014m8p26g.png)

**5.2 选择申请类型**
  Development作为开发使用，Distribution作为发布使用，以下都为发布证书的图例演示；选择In-House点击Continue按钮进入下一步。（注意，和发布证书类型保持一致。）
![](http://newdocx.appcan.cn/docximg/194408x2014p8h26c.png)

**5.3 选择申请文件对应App ID**
  点击下拉菜单，选择要申请的App ID，点击Continue按钮进入下一步。
![](http://newdocx.appcan.cn/docximg/194352s2014n8o26w.png)

**5.4 选择申请的发布证书**
  选择发布证书选项，点击Continue按钮进入下一步。
![](http://newdocx.appcan.cn/docximg/194336r2014m8r26k.png)

**5.5 保存Provisioning Profiles文件标签**
  Profile Name填入描述文字，只能输入英文，点击Generate按钮创建provisioning文件。等待几秒钟，provisioning就可以下载了， 点击download下载。得到了一个xxxxxx.mobileprovision文件，AppCan.cn在线ipa包编译时需要上传的 distribution.mobileprovision就是您生成的文件。
![](http://newdocx.appcan.cn/docximg/194323n2014z8s26z.png)

#6．iOS证书导出

**6.1 证书导入到钥匙串程序中**
  点击“download”下载您生成的证书。下载完成后双击证书安装，或拖动到钥匙串访问窗口，就可以看到您申请的证书了。推送证书和发布证书都在列表中，在证书上单击右键，在弹出菜单上选择导出选项：
![](http://newdocx.appcan.cn/docximg/194306p2014r8b26v.png)

**6.2 证书保存为.P12为扩展名的文件**
  给导出的证书起个名字，选择存储的位置。（注意，格式为P12的信息交换文件。）
![](http://newdocx.appcan.cn/docximg/194253b2014p8r26c.png)

**6.3 p12文件添加密码**
  给导出的P12文件设置密码，此密码在AppCan.cn平台上打包ipa文件时需要用到。
![](http://newdocx.appcan.cn/docximg/194238c2014m8b26w.png)