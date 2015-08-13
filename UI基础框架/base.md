[TOC]

  ##CSS Variables
  ### 圆角类别
**定义：**
uc-[类型][类型][类别]......
**说明：**
前缀为uc-，代表UI CORNER
类型为t带表TOP，l代表LEFT，b代表BOTTOM，r代表RIGHT，a代表ALL
类别为数字编号，用于定义不同大小的圆角
**例子：**
> 
uc-t代表上圆角即左上和右上圆角。类别为空，定义的为圆角半径为0.6em的圆角
uc-tl代表左上圆角。类别为空，定义的为圆角半径为0.6em的圆角
uc-t1代表上圆角即左上和右上圆角。类别为空，定义的为圆角半径为0.3em的圆角

**场景：**

```
<div class='btn uba b-bla uinn5 c-blu c-m1 uc-a t-wh'>确定</div>
```

**图例：**
![](http://newdocx.appcan.cn/docximg/105153e2014y8r4h.png) 


   
  ###   外阴影类别
**定义：**
us[类别]......
**说明：**
前缀为us，代表UI SHADOW
类别为数字编号，用于定义不同大小和不同颜色的外阴影
**例子：**
> 
us代表外阴影。类别为空，定义的外阴影颜色为黑色
us1代表外阴影。类别为1，定义外阴影颜色为灰白色

**场景：**
```
<div class='btn uba b-bla uinn5 c-blu2 c-m1 uc-a t-wh us'>确定</div>```
**图例：**

（使用us外阴影效果）
![](http://newdocx.appcan.cn/docximg/105207t2014b8g4n.png) 
（未使用us外阴影效果）
![](http://newdocx.appcan.cn/docximg/105217p2014k8i4v.png) 


 ### 内阴影类别
**定义：**
us-i[类别]......
**说明：**
前缀为us-i，代表UI SHADOW INSET
类别为数字编号，用于定义不同大小和不同颜色的内阴影
**例子：**
us-i代表内阴影。类别为空，定义内阴影大小及阴影颜色为黑色
**场景：**
```
<div class='btn uba b-bla uinn5 c-blu2 c-m1 uc-a t-wh us-i'>确定</div>```

**图例：**
![](http://newdocx.appcan.cn/docximg/113156z2014u8y4i.png) 
             

   
 ### 文字阴影
**定义：**
uts......
**说明：**
用于定义文字的阴影效果
**例子：**
uts代表内阴影。定义文字阴影大小及阴影颜色
**场景：**
```
<div class='btn uba uc-a b-bla uinn5 c-blu2 c-m1 t-wh uts'>确定</div>```
**图例：**
![](http://newdocx.appcan.cn/docximg/172423c2014n8a17b.jpg) 


  
###     body样式
**定义：**
um-vp......
**说明：**
> 
um-vp代表UI MOBILE VIEWPORT
um-vp定义body的内边距padding，外边距margin的大小以及文字大小可以调整，超过body宽度的部分隐藏

**场景：**
```
<body class='um-vp'></body>```

   
  ### 页面样式
**定义：**
up......
**说明：**
up，代表UI PAGE
up一般和um-vp搭配使用，用于定义页面大小自适应手机屏幕大小
**场景：**
```
<body class='um-vp'><div class='up'></div></body>```

 
 ###  跟头部和底部有关的样式
**定义：**
.uh,.uf
.up .uh,.up .uf
**说明：**
> 
uh，代表UI HEADER
uf，代表UI FOOTER
uh和uf定义头部和底部的元素的一些基本属性

**场景：**
```
<div id='page_0' class='up ub ub-ver' tabindex='0'>
<!--header开始-->
<div id='header' class='uh c-org c-m1 t-wh'>
<h1 class='ut ulev0 ut-s tx-c' tabindex='0'>AppCan</h1>
</div>
<!--header结束-->
<!--content开始-->
<div id='content' class='ub-f1 tx-l uinn2 t-bla ub-img6 res10'>
</div>
<!--content结束-->
<!--footer开始-->
<div id='footer' class='uf c-m2 c-bla t-wh'>
<h1 class='ut ulev-2 tx-c' tabindex='0'>(c) Copyright 3G2WIN and others 2011.
<br>
All rights reserved.
</h1>
</div>
<!--footer结束-->
</div>```

**图例：**
![](http://newdocx.appcan.cn/docximg/114855i2014t8q4g.png) 
 

   
 
  ###  头部和底部内文本区域的样式
**定义：**
.ut......
**说明：**
ut，代表UI TITLE
定义头部和底部的内边距和外边距的大小
**场景：**
```
<div id='header' class='uh c-org c-m1 t-wh'>
<h1 class='ut ulev0 ut-s tx-c' tabindex='0'>AppCan</h1>
</div>
<div id='footer' class='uf c-m2 c-bla t-wh'>
<h1 class='ut ulev-2 tx-c' tabindex='0'>
(c) Copyright 3G2WIN and others 2011.
<br>
All rights reserved.
</h1>
</div>```
 
   
   
###     浮动类别
 **定义：**
uf[类型]......
**说明：**
前缀为uf，代表UI FLOAT
类型为l代表LEFT，r代表RIGHT
用于定义元素的浮动方向
**例子：**
> 
ufl代表元素左浮动
ufr代表元素右浮动

  
   
  ### 字体大小类别
**定义：**
ulev[类别]......
**说明：**
前缀为ulev
类别为数字编号，用于定义不同大小的字体；其中数值越大代表字体大小越大，数值越小代表字体大小越小
**例子：**
> 
ulev0类别为0，定义的字体大小为1em
ulev1类别为1，定义的字体大小为1.2em
ulev-1类别为-1，定义的字体大小为0.8em

**场景：**
```
<div class=' ulev2 uinn c-blu c-m1 uc-a1 tx-c t-wh'>确定</div>
<div class=' ulev-1 uinn c-blu c-m1 uc-a1 tx-c t-wh'>确定</div>
```

**图例：**
![](http://newdocx.appcan.cn/docximg/114907y2014o8i4l.png) 
![](http://newdocx.appcan.cn/docximg/114919w2014q8k4l.png) 

 

 ###  限制宽度大小
**定义：**
ulim......
**说明：**
ulim定义元素的最大宽度超过部分省略
**场景：**
```
<div class=' ulim ulev-1 uinn5 c-blu c-m1 uc-a1 tx-c t-wh'>确定确定确定确定确定确定</div>```

**图例：**
![](http://newdocx.appcan.cn/docximg/154817n2014g8i4n.png)      

   
 ###单行类别
**定义：**
uinl......
**说明：**
用于定义元素为行内元素
**场景：**
```
<div class='btn uba b-bla uinn2 uinl c-blu c-m1 uc-a t-wh'>确定</div>```

**图例：**
![](http://newdocx.appcan.cn/docximg/154829g2014r8c4g.png) 
（未使用uinl）
![](http://newdocx.appcan.cn/docximg/154838g2014f8l4y.png) 
（使用uinl）
 
 
   
 ### 内边距类别
**定义：**
uinn[类别]......
**说明：**
前缀为uinn
类别为数字编号，用于定义不同内边距的大小
**例子：**
> 
uinn类别为空，定义的内边距大小上右下左均为0.5em
uinn1类别为1，定义的内边距大小上下为0，左右为0.5em

**场景：**
```
<div class='btn uba b-bla uinn c-blu c-m1 uc-a t-wh'>确定</div>
```

**图例：**
![](http://newdocx.appcan.cn/docximg/154854u2014u8f4g.png) 
（使用uinn）
![](http://newdocx.appcan.cn/docximg/154904e2014y8n4n.png) 
（使用uinn5）

   
 ### 最小高度类别
**定义：**
umh[类别]......
**说明：**
前缀为umh
类别为数字编号，用于定义不同大小的最小高度
**例子：**
> 
umh1类别为1，定义最小高度为1em
umh2类别为2，定义最小高度为1.2em

**场景：**
```
<div class=' tx-c umh1 uinn c-bla c-m1 uc-a t-wh'>确定</div>
```

**图例：**
![](http://newdocx.appcan.cn/docximg/154919b2014q8l4n.png) 
（使用umh1）
![](http://newdocx.appcan.cn/docximg/154932p2014s8d4l.png) 
（使用umh3）
 


 ### 最小宽度类别
**定义：**
umw[类别]......
**说明：**
前缀为umw
类别为数字编号，用于定义不同大小的最小宽度
**例子：**
> 
umw1类别为1，定义最小宽度为1em
umw2类别为2，定义最小宽度为2em

**场景：**
```
<div class=' uinn uinl c-bla umw1 c-m1 uc-a t-wh'>确定</div>```

**图例：**

 ![](http://newdocx.appcan.cn/docximg/174003r2014c8q4f.png) 
（使用uww1） 
  ![](http://newdocx.appcan.cn/docximg/174018h2014h8u4i.png) 
                   （使用umw3）


 ### 文字对齐方向
**定义：**
tx-[类型]......
**说明：**
前缀为tx-
类型为l代表LETT,r代表RIGHT,c代表CENTER
用于定义文字的对齐方向
**例子：**
> 
tx-l代表左对齐
tx-r代表右对齐
tx-c代表居中对齐

**场景：**
```
<div class=' uinn c-blu2 c-m1 uc-a1 tx-l t-wh'>确定</div>```

**图例：**
![](http://newdocx.appcan.cn/docximg/174032g2014g8r4u.png) 
（使用tx-l）
![](http://newdocx.appcan.cn/docximg/173341g2014w8s17o.jpg) 
（使用tx-c）
 

 ### 超出指定宽度隐藏并且文字不换行
**定义：**
ut-s......
**说明：**
用于定义文字超过容器指定宽度时文字隐藏并且文字不换行
**场景：**

```
<div class='uinn c-blu2 c-m1 uc-a1 tx-c ut-s t-wh' style='width:5em;'>确定确定确定确定</div>
```

**图例：**

 ![](http://newdocx.appcan.cn/docximg/174852c2014h8p4y.png) 

 ### 边框类别
**定义：**
ub[类型] [类别]......
**说明：**
前缀为ub
类型为t带表TOP，l代表LEFT，b代表BOTTOM，r代表RIGHT，a代表ALL
类别为数字编号，用于定义不同大小的边框
**例子：**
> 
ub-t代表上边框。类别为空，定义的边框宽度为1px
ub-l代表左边框。类别为空，定义的为边框宽度为1px
uba代表四个边的边框。类别为空，定义的边框宽度为1px
uba1代表四个边的边框。类别为1，定义的边框宽度为2px

**场景：**
```
<div class='uba b-bla uinn c-blu c-m1 uc-a1 tx-c t-wh'>确定</div>
<div class='uba1 b-bla uinn c-blu c-m1 uc-a1 tx-c t-wh'>确定</div>
```

**图例：**
![](http://newdocx.appcan.cn/docximg/174013o2014n8s17s.jpg) 
 
 
 
 
###  隐藏元素
**定义：**
uhide......
**说明：**
代表元素隐藏display属性为none
**场景：**
```
<div class='uhide '>确定</div>```
 
 
 
 
###     外边距类别
**定义：**
umar-[类型]......
**说明：**
定义外边距的大小
类型为t代表TOP定义上边距大小， b代表BOTTOM定义下边距大小，l代表LEFT定义左边距大小，r代表RIGHT定义右边距大小，a代表ALL定义上、下、左、右四个方向的边距大小
**例子：**
> umar-t代表上边距。定义的上边距的大小为margin-top：0.4em
umar-b代表下边距。定义的下边距的大小margin-bottom:0.4em
umar-l代表左边距。定义的下边距的大小margin-left:0.4em
umar-r代表下边距。定义的右边距的大小margin-right:0.4em
umar-a代表上下左右四个边的边距。定义margin：0.4em

**场景：**
```
<div class='btn b-bla uba uinn5 c-blu c-m1 uc-a1 tx-c t-wh'>确定</div>
<div class='btn uba b-bla umar-t uinn5 c-blu c-m1 uc-a1 t-wh'>确定</div>```
**图例：**
![](http://newdocx.appcan.cn/docximg/174926g2014v8l4g.png) 
 
 
 
###     内容溢出元素框时，超出的部分隐藏
**定义：**
uof-[类型]......
**说明：**
> uof-x：类型为x时，定义oveflow-x：hidden；超出容器的指定宽度时，横向超出的部分隐藏
uof-y：类型为y时，定义oveflow-y：hidden；超出容器的指定高度时，纵向超出的部分隐藏
uof：类型为空时，定义overflow：hidden；内容溢出元素框时，溢出的部分隐藏
 
 
 
 
 
 
 ### 定位元素
**定义：**
uabs......
**说明：**
定义元素位于页面的左上角，```position:absolute;left:0px; top:0px;```