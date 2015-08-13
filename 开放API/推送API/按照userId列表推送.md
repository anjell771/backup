[TOC]

#1、接口授权authtoken生成流程说明


##1.1、 生成规则
> 当调用AppCan推送相关接口时，我们需要对头部信息中authtoken进行验证，authtoke 的生成规则如下：授权token 是在个人中心开启，[开启授权token](http://i.appcan.cn/Apply.html)

# 2、请求结构
## 2.1、接口说明
> 注：如果是ios推送需要先在appcan.cn上上传相应的推送证书

##2.2、服务地址

> `http://newpush.appcan.cn/oauth/sendByUid`

##2.3、请求方式

> 使用 POST

##2.4、参数
> authtoken 授权token ------ 例如：deb12c85-b675-b77b-2cfd-f6f0cd7219a5
email 用户邮箱 ------例如：test@test.com
appId 应用Id ------ 例如：11387747
platforms 推送平台，1：android;0：ios，默认0，1
userIdListStr 推送用户的userId列表, 例如：1,2,3,4 （每一个userId用逗号隔开）userId相关接口为uexWidget.setPushInfo(uId, uNickName)方法的第一个参数，参考文档 [点击跳转](http://newdocx.appcan.cn/newdocx/docx?type=1251_1249#setPushInfo 设置推送用户信息)  uexWidget。
title 推送消息内容
body {"msgName":"推送消息标题"} --- 必须为json数据

##2.5、请求编码
> 请求及返回结果都是返回json数据：status: ok/ failed info：描述信息。
成功返回： {"status":"ok","info":"push success"}

##2.6、错误码标识

标识的意义
> * -1: appId 参数不能为空
* -2: ios推送中需要上传p12证书 ````注：证书上传需要到对应的项目应用下的推送页面（应用管理）操作 ````
* -3: appId 无效 
* -4: 内部解析错误（多数因为body不是合法的json字符串） 
* -5: 推送内容过长 
* -6: android终端用户不存在
* -7: ios终端用户不存在