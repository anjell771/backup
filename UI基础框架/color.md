[TOC]

### 概述
UI3.0颜色类，默认提供的基础类名在ui-color.css，需要在IDE工具可视化配置，即先定义主题色，设置模板主题，中国红、蜜桃粉、青草绿、天际蓝、子夜灰


  ## CSS Variables
   
  ### 背景色类别

**定义：**
bc-head
bc-bg
sc-bg
sc-bg-active
sc-bg-alert

**说明：**
> bc-head类别: 基础header颜色;定义了header区域背景底色,在ui3.0框架中,IDE工具可以可视化配置
bc-bg类别: 基础body背景颜色; 定义了body背景底色,在ui3.0框架中,IDE工具>插入控件,可视化配置
sc-bg类别: 辅助控件背景颜色1; 定义了辅助控件背景底色,在ui3.0框架中,IDE工具>插入控件,可视化配置
sc-bg-active类别: 辅助控件背景颜色2; 定义了辅助控件背景底色,在ui3.0框架中,IDE工具>插入控件,可视化配置
sc-bg-alert类别: 警告背景色; 定义了header区域背景底色,在ui3.0框架中,IDE工具>插入控件,可视化配置

**场景：**
 
![](http://newdocx.appcan.cn/docximg/144334i2015g6o1c.jpg)
![](http://newdocx.appcan.cn/docximg/152810t2015m6t1i.jpg)
**例子：**
````
<!--header开始-->
            <div id="header" class="uh bc-text-head ub bc-head"></div>
            <!--header结束--> ````
**图例：**

 ![](http://newdocx.appcan.cn/docximg/153727o2015k6k1l.jpg)
 
### 按钮颜色类别
** 定义：**
bc-btn
sc-btn

**说明：**
> bc-btn 基础按钮颜色 应用的是主题颜色
sc-btn 辅助按钮颜色 应用的是主题颜色

 类别分别用于定义不同颜色值,默认提供的字体颜色可以自己灵活应用,也可自定义

**场景：**
 ui-color.css中 鼠标定位颜色属性上可查看颜色

 
**例子：**
````
<div class='btn ub ub-ac bc-text-head ub-pc bc-btn'>确定</div>````
**图例：**
![](http://newdocx.appcan.cn/docximg/173330l2015f6w1q.jpg)
 
 
###文字色彩类别
** 定义：**
bc-text 
bc-text-head
sc-text
sc-text-active
sc-text-hint
sc-text-warn
sc-text-tab

**说明：**
> bc-text 基础字体颜色 black
bc-text-head 基础标题字体颜色 white
sc-text 辅助字体颜色1 #848484
sc-text-active 辅助字体颜色2 应用的是主题颜色
sc-text-hint 辅助字体颜色3 
sc-text-warn 辅助字体颜色4
sc-text-tab 辅助字体颜色5

 类别分别用于定义不同色彩，默认提供的字体颜色可以自己灵活应用,也可自定义

**场景：**
ui-color.css中 鼠标定位颜色属性上可查看颜色

![](http://newdocx.appcan.cn/docximg/170024s2015o6g1g.jpg)![](http://newdocx.appcan.cn/docximg/170030q2015v6n1g.jpg)![](http://newdocx.appcan.cn/docximg/170140u2015o6s1v.png)
**例子：**
````
<div class= "btn ub ub-ac bc-text-head ub-pc bc-btn " id="btn">无图片按钮</div>  ````

**图例：**
![](http://newdocx.appcan.cn/docximg/170833x2015i6u1d.jpg)

 


###边框色彩类别

** 定义：**
bc-border
sc-border
sc-border-tab

**说明：**
> bc-border 基础边框颜色 默认是#BABABA
sc-border 辅助边框颜色 默认是#FFFFFF
sc-border-tab 辅助边框颜色 应用的是主题颜色

 类别分别用于定义不同色彩， 默认提供的边框颜色可以自己灵活应用,也可自定义

**场景：**
ui-color.css中 鼠标定位颜色属性上可查看颜色

  

**例子：**
````
<div id="listview"class="ubt bc-border sc-bg"> </div> ```` 
**图例：**
![](http://newdocx.appcan.cn/docximg/171607q2015e6y1x.png)