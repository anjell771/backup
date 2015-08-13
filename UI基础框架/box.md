[TOC]

### 概述 
UI3.0使用弹性盒子对页面进行布局，ui-box.css中就定义了弹性盒子的一些css3样式，弹性盒子模型是在指定大小的父容器里来为子元素分配空间，使用box架构可以更容易更方便的适配不同分辨率不同屏幕尺寸的手机


##   CSS Variables
###  Box架构
**定义：**
ub......
**说明：**
使用box弹性盒子模式对页面进行布局
**例子：**
ub定义元素的display属性为box。那么子元素就可以根据我们定义的比例来分配元素的空间，ub一般跟ub-f[1-4]搭配着使用


 ###Box架构元素空间大小分配比例
**定义：**
ub-f......
**说明：**
定义不同的box-flex属性值
类别使用数字编号，定义不同的元素空间大小分配比例
**例子：**
> ub-f1数字编号为1；定义box-flex：1
ub-f1数字编号为2；定义box-flex：2
ub-f1数字编号为3；定义box-flex：3
ub-f1数字编号为4；定义box-flex：4
ub-f[1-4]和ub搭配着使用

**解析：**
1、若子元素都使用ub-f1，那么子元素等比例的分配父元素的空间大小
````
<div class='ub c-gra uba b-bla umh5'>
 <div class='ub-f1 sc-bg-alert'></div>
 <div class='ub-f1 bc-head'></div>
</div>````
![](http://newdocx.appcan.cn/docximg/181813e2015i6v1p.jpg)

2、若子元素一个用ub-f1，另外一个用ub-f2.，那么子元素按照1：2的比例分配父元素的空间大小
````
<div class='ub c-gra uba b-bla umh5'>
 <div class='ub-f1 sc-bg-alert'></div>
 <div class='ub-f2 bc-head'></div>
</div>````
![](http://newdocx.appcan.cn/docximg/181821p2015m6f1e.jpg)
3、若子元素分别使用ub-f1，ub-f2，ub-f3，那么子元素会按照1：2：3的比例分配父元素的空间大小
````
<div class='ub c-gra uba b-bla umh5'>
 <div class='ub-f1 sc-bg-alert'></div>
 <div class='ub-f2 bc-head'></div>
 <div class='ub-f3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/181831a2015b6g1q.jpg)
4、若子元素中只有一个使用ub-f1，另外一个元素根据内容的多少定义大小，那么使用ub-f1的元素会自动适配元素的剩余空间大小
````
<div class='ub c-gra uba b-bla umh5'>
 <div class='sc-bg-alert'>内容</div>
 <div class='ub-f1 bc-head'></div>
</div>````
  ![](http://newdocx.appcan.cn/docximg/182008q2015l6t1r.jpg)           

ub-f[1-4]和ub搭配着使用
**场景：**
````
<div class='uba b-gra c-wh us uc-a '>
<div ontouchstart='zy_touch('btn-act')' class='uc-t ubb ub b-gra t-bla ub-ac lis umh4'>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
<div ontouchstart='zy_touch('btn-act')' class=' ub ubb b-gra t-bla ub-ac lis umh4'>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
<div ontouchstart='zy_touch('btn-act')' class='uc-b ub t-bla ub-ac lis umh4'>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
</div>````
**图例：**
![](http://newdocx.appcan.cn/docximg/185457n2014d8u4g.png)
 


###Box架构元素垂直方向的位置排列
**定义：**
ub-ac，ub-ae......
**说明：**
> ub-ac：垂直居中
ub-ae：位于底边
只有跟ub搭配着使用ub-ac，ub-ae的作用才生效

**例子：**
1、未使用ub-ac，ub-ae
````
<div class='ub uinn umh4 uba b-gra uc-a'>
 <div class='ub-f1'>内容</div>
 <div class='res8 lis-sw ub-img'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/191816k2014g8k4p.png)
2、使用ub-ac
````
<div class='ub uinn umh4 uba b-gra uc-a ub-ac'>
 <div class='ub-f1'>内容</div>
 <div class='res8 lis-sw ub-img'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/191826d2014x8u4c.png)
3、使用ub-ae
````
<div class='ub uinn umh4 uba b-gra uc-a ub-ae'>
 <div class='ub-f1'>内容</div>
 <div class='res8 lis-sw ub-img'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/191837m2014k8o4s.png)
**场景：**
````
<div class='uba b-gra c-wh us uc-a '>
 <div ontouchstart='zy_touch('btn-act')' class='uc-t ubb ub b-gra t-bla ub-ac lis'>
 <div class='lis-icon ub-img im'></div>
 <div class='ub-f1 ut-s'>设置</div>
 <div class='tx-r t-blu ulev-1'>Old Phone</div>
 <div class='res8 lis-sw ub-img'>></div>
 </div>
 <div ontouchstart='zy_touch('btn-act')' class=' ub ubb b-grat-bla ub-ac lis'>
 <div class='lis-icon ub-img im'></div>
 <div class='ub-f1 ut-s'>设置</div>
 <div class='tx-r t-blu ulev-1'>Old Phone</div>
 <div class='res8 lis-sw ub-img'></div>
 </div>
 <div ontouchstart='zy_touch('btn-act')' class='uc-b ub t-bla ub-ac lis'>
 <div class='lis-icon ub-img im'></div>
 <div class='ub-f1 ut-s'>设置</div>
 <div class='tx-r t-blu ulev-1'>Old Phone</div>
 <div class='res8 lis-sw ub-img'></div>
</div>
 </div>
 ````
**图例：**
![](http://newdocx.appcan.cn/docximg/191850k2014c8k4d.png)
 
 


### Box架构元素水平方向的位置排列
**定义：**
ub-pc，ub-pe，ub-pj......
**说明：**
> ub-pc：水平居中
ub-pe：位于末尾
ub-pj：两端对齐
只有跟ub搭配着使用ub-pc，ub-pe，ub-pj的作用才生效

**例子：**
1、未使用ub-pc，ub-pe，ub-pj
````
<div class='uinn2 c-gra ub'> <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/175120e2015l6v1i.png)

2、使用ub-pc
````
<div class='uinn2 c-gra ub-pc ub uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/175129a2015o6k1c.jpg)
3、使用ub-pe
````
<div class='uinn2 c-gra ub-pe ub uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/175135h2015x6g1i.png)
4、使用ub-pj
````
<div class='uinn2 c-gra ub-pj ub uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/175144f2015h6f1k.png)
 

###  Box架构元素垂直排列
**定义：**
ub-ver....
**说明：**
ub-ver：定义元素垂直排列
只有跟ub搭配着使用ub-ver的作用才生效
**例子：**
1、未使用ub-ver
````
<div class='uinn2 c-gra ub uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/092306t2015g6z2g.png)
2、使用ub-ver
````
<div class='uinn2 c-gra ub ub-ver uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/175926s2015y6y1g.png)



###Box架构元素排列方向
**定义：**
ub-rev......
**说明：**
ub-rev：定义元素排列方向
只有跟ub搭配着使用ub-rev的作用才生效
**例子：**
1、未使用ub-rev
````
<div class='uinn2 c-gra ub uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/180236w2015c6e1m.png)

2、使用ub-rev
````
<div class='uinn2 c-gra ub ub-rev uba b-bla'>
 <div class='umh5 umw3 sc-bg-alert'></div>
 <div class='umh5 umw3 bc-head'></div>
 <div class='umh5 umw3 sc-bg-active'></div>
</div>
````
![](http://newdocx.appcan.cn/docximg/180326m2015o6k1s.png)
 


### Box架构实现横向滑动效果

**定义：**
ub-fh......
**说明：**
在box架构中ub-fh一般跟函数zyFlip（）搭配着使用实现横向滑动效果


### Box架构实现纵向滑动效果

**定义：**
ub-fv......
**说明：**
在box架构中ub-fv一般跟函数iScroll（）搭配着使用实现纵向滑动效果

### 背景图片类别
**定义：**
ub-img[类别]......
**说明：**
前缀为ub-img
类别为数字编号，用于定义不同的背景排列方式
**例子：**
> ub-img类别为空，定义将背景图像等比缩放到宽度或高度与容器的宽度或高度相等，背景图像始终包含在容器内
ub-img1类别为1，定义将背景图片等比例缩放到完全覆盖容器，背景图像有可能超过容器
ub-img2类别为2，定义背景图像横向平铺
ub-img3类别为3，定义背景图像纵向平铺
ub-img4类别为4，定义背景图像横向100%，纵向自适应;
ub-img5类别为5，定义背景图像横向自适应，纵向为100%
ub-img6类别为6，定义背景图像居中显示

**场景：**
````
<div class='uba b-gra c-wh us uc-a '>
<div ontouchstart='zy_touch('btn-act')' class='uc-t ubb ub b-gra t-bla ub-ac lis'>
<div class='lis-icon ub-img im'></div>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
<div ontouchstart='zy_touch('btn-act')' class=' ub ubb b-gra t-bla ub-ac lis'>
<div class='lis-icon ub-img im'></div>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
<div ontouchstart='zy_touch('btn-act')' class='uc-b ub t-bla ub-ac lis'>
<div class='lis-icon ub-img im'></div>
<div class='ub-f1 ut-s'>设置</div>
<div class='tx-r t-blu ulev-1'>Old Phone</div>
<div class='res8 lis-sw ub-img'></div>
</div>
</div>
````
**图例：**
![](http://newdocx.appcan.cn/docximg/192850n2014g8l4e.png)