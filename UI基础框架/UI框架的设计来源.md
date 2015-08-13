[TOC]

### 概述
　弹性盒子模型是CSS推出的一种布局机制。这种机制与常见的流式布局有很大区别。简单的理解为，流式布局是通过内容决定父容器大小，弹性盒子模型是，在指定大小的父容器里来为子元素分配空间，简单的流式布局例子。
**效果：**
![](http://docx.appcan.cn/output/images/004.png) 
**示例：**
```
<div style='display:inline;border:1px solid blue'>
<div style='display:inline;background:#E00'>aaaa </div>
<div style='display:inline;background:#0E0'>bbbb </div>
</div>
```
上述代码中是一个简单的流式布局范例，第1行的div的宽度，是由第2和第3行的div宽度相加来决定的。即如果第2行或第3行的div宽度变化，第1行的宽度也会随之变化。 我们调整一下代码，使用弹性盒子模型来布局。
**效果：**
![](http://docx.appcan.cn/output/images/006.png) 
**示例：**
```
<div style='display:-webkit-box;width:200px;border:1px solid blue'>
<div style='-webkit-box-flex:1;background:#E00'>aaaa </div>
<div style='background:#0E0'>bbbb </div>
</div>```
上 述代码中，指定第1行的div使用BOX方式布局子元素。并指定这个div宽200px。第3行的div的宽度由内容撑开，可以认为是一个指定宽度的 div，通过模拟器可以看到宽32px。第2行指定这个div为弹性，占用1份空间,就代表这个div的宽度是总宽度200px-32px=168px。 如果我们改动第1行的div宽度为320px，那么第2行div的宽度就是 320px-32px=288px。这个机制对于适配各种分辨率的屏幕无疑是一把利器。
我们再调整一下代码。
**效果：**
![](http://docx.appcan.cn/output/images/008.png) 
**示例：**
```
<div style='display:-webkit-box;width:200px;border:1px solid blue'>
<div style='-webkit-box-flex:1;background:#E00'>aaaa </div>
<div style='-webkit-box-flex:2;background:#0EE'>bbbb </div>
<div style='background:#0E0'>cccc </div>
</div>```
我 们加入了一个占用2份空间的div。这个时候这两个弹性DIV到底如何分配空间呢？按照规则来说，第2行应该占用168px/3=56px，第3行占用 112px，但实际上宽度并不是如此， 通过模拟器可以看到，第34行占用66px，第35行占用102px。这是由于当弹性DIV中有内容时，引擎会自动进行调整。那么如何在有内容的情况下还 能够保持1：2的比率呢？ 我们再调整一下代码。
**效果：**
![](http://docx.appcan.cn/output/images/009.png) 
**示例：**
```
<div style='display:-webkit-box;width:200px;border:1px solid blue'>
<div style='-webkit-box-flex:1;background:#E00;position:relative'>
<div style='position:absolute;width:100%;height:100%;'>aaaa </div>
</div>
<div style='-webkit-box-flex:2;background:#0EE;position:relative'>
<div style='position:absolute;width:100%;height:100%;'>bbbb </div>
</div>
<div style='background:#0E0'>cccc </div>
</div>```
这次修改中，我们把内容'aaaa'通过一个使用绝对定位的div进行包含，这时通过模拟器去看会发现，两个弹性div按照1:2的比率自动分配了空间。 上面我们使用弹性盒子布局时元素都是横向排序的，那么怎么才能让元素纵向排布呢。我们接着调整一下代码。
**效果：**
![](http://docx.appcan.cn/output/images/010.png) 
**示例：**
```
<div style='display:-webkit-box;height:200px;border:1px solid blue;-webkit-box-orient:vertical;'>
<div style='-webkit-box-flex:1;background:#E00;position:relative'>
<div style='position:absolute;width:100%;height:100%;'>aaaa </div>
</div>
<div style='-webkit-box-flex:2;background:#0EE;position:relative'>
<div style='position:absolute;width:100%;height:100%;'>bbbb </div>
</div>
<div style='background:#0E0'>cccc </div>
</div>
```
上述代码中，我们在第1行的div中指定了高度为200px，使用-webkit-box-orient:vertical来控制子元素为纵向排列。弹性盒子模型还提供了其他几个强大的属性。
### 1、弹性盒子模型还提供了其他几个强大的属性
-webkit-box-direction:reverse;
通过在父DIV中设定这个属性可以让子元素反向排列。如下图：
![](http://docx.appcan.cn/output/images/011.png) 
使用前子元素按照1 2 3 的顺序进行排列显示，当在父DIV中使用此属性时，自动把子元素倒序排列。这个时候，我们并没有真的重新按照3 2 1顺序排布子元素。
-webkit-box-align:center;
通过在父元素中设定这个属性，当子元素横向排布时，可以使子元素间实现上边界对齐、中线对齐和下边界对齐的效果。
![](http://docx.appcan.cn/output/images/012.png) 
如果是纵向排列时，那么可以实现子元素左边界对齐、中线对齐和右边界对齐。
![](http://docx.appcan.cn/output/images/013.png) 
-webkit-box-pack:center;
通过在父元素中设定这个属性，当子元素横向排布时，可以使子元素间左边界对齐、中线对齐和右边界对齐。
![](http://docx.appcan.cn/output/images/013.png) 
如果是纵向排列时，那么可以实现子元素间上边界对齐、中线对齐和下边界对齐的效果。
![](http://docx.appcan.cn/output/images/012.png) 
如果父元素中只包含一个子元素，混合使用-webkit-box-align和 -webkit-box-pack可以使子元素实现居左上、居中上、局右上等9个方位的定位。
弹性BOX架构可以同时兼容流式布局，即当所有子元素都没有设定弹性份数时，父元素可以被子元素自动撑开。如下代码
**效果：**
![](http://docx.appcan.cn/output/images/014.png) 
**示例：**
```
<div style='display:-webkit-box;border:1px solid blue;-webkit-box-orient:vertical;'>
<div>aaaa </div>
<div>bbbb </div>
<div>cccc </div>
</div>
```
在上述代码中所有子元素都未使用box-flex定义弹动属性，容器div也未设定高度，此时，容器div的高度为三个子元素的高度和，并且随着子元素的高度变化而变化。
在AppCan UI架构中，我们把上面遇到的情况进行了CSS类封装
ub 元素采用弹性BOX布局
ub-rev 子元素反序排列
ub-con 在子元素中加入一个容器，用于避免内容引起子元素大小变化
对应CSS代码为position:absolute;width:100%;height:100%;
ub-ac、ub-ae 子元素垂直居中对齐和尾对齐
ub-pc、ub-pe、ub-pj 子元素水平居中对齐、尾对齐和两端对齐
ub-ver 子元素纵向排列
ub-f1 ub-f2 ub-f3 ub-f4 子元素占用区域份数
通过上述类，我们可以完成各种各样的排版布局，极大地降低学习难度和元素排版复杂度，使代码更加简练。
### 2、基石 (UI的分辨率适配)
每 一个手机应用，如果需要在众多的移动终端上保持一致的效果，UI适配是工作的重中之重。设计原理是为不同分辨率的系统，选取最贴近于人直观感受舒适度的一 个字体大小作为参考量。例如在320x480分辨率的手机上，采用16px大小字体作为参考量。在480x800分辨率的终端上，采用24px大小字体作 为参考量。一切元素的大小都是以参考量的相对比值来定义。在CSS里面对应的是em。那么在320x480分辨率下 1em=16px，在480x800分辨率下1em=24px。

通过这种方式，我们可以保证，同样代码的界面，在不同分辨率下都能够保持最贴近用户的交互效果。

UI 中，我们在中间件中为不同屏幕密度(单位尺寸中可显示的点数)，默认定义好了字体，开发者不再需要在代码中引入ui-media.css文件，即使有新的 分辨率手机问世，也会自动适配。目前参照Andorid屏幕密度划分为低密度、普通密度、高密度、超高密度、超超高密度，分别定义字体为14px 16px 24px 32px 48px。