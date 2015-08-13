[TOC]



###1、应用简介
该应用会一步一步给你演示怎么开发一个AppCan应用。该应用包含最常用的插件，window、request、file等。另外教会你使用AppCan应用开发平台，AppCan IDE等相关知识。
 
###2、开发环境
首先去AppCan官网下载并安装AppCan IDE
<a href="http://newdocx.appcan.cn/newdocx/docx?type=1236_1234">安装下载</a>


如果开发AppCan应用，可以直接在IDE中新建项目开发，然后打包成应用，另外可以通过在AppCan的官方网站上创建应用在在IDE中开发完成后到官网上进行打包。

1）、注册并登陆AppCan应用管理系统（[http://dashboard.appcan.cn/app](http://dashboard.appcan.cn/app) ）。
  ![](http://newdocx.appcan.cn/docximg/180236v2014l9a22d.jpg) 
 
2）、点击创建应用。
  ![](http://newdocx.appcan.cn/docximg/180245k2014m9x22q.jpg) 
 
3）、 输入你的应用名称，和应用描述，然后保存。
  ![](http://newdocx.appcan.cn/docximg/180252n2014v9a22e.jpg) 
 
4）、点击天气，进入天气应用的详细信息。
  ![](http://newdocx.appcan.cn/docximg/180259b2014d9v22q.jpg) 
 
5）、打开AppCan IDE，并用刚才注册的用户登陆
  ![](http://newdocx.appcan.cn/docximg/180306y2014g9c22s.jpg) 
 
5）、登录进入IDE
  ![](http://newdocx.appcan.cn/docximg/180313v2014n9b22t.jpg) 

6）、点击新建项目
  ![](http://newdocx.appcan.cn/docximg/180321y2014g9u22k.jpg) 

7）、选择同步AppCan 项目，点击下一步。
  ![](http://newdocx.appcan.cn/docximg/180328d2014i9x22u.jpg) 

8）、选择天气点击完成。
  ![](http://newdocx.appcan.cn/docximg/180338e2014i9i22u.jpg) 
  
9）、整个应用创建完成了。
   
###3、应用开发
 1) 、打开index.html页面加入应用头部，我们的头部都是统一的，所以加入一下代码
  ```
 <!--header开始-->
<div id="header" class="uh bc-text-head ubbc-head">
<div class="nav-btn" id="nav-left">
</div>
<h1 class="ut ub-f1 ulev-3 ut-s tx-c" tabindex="0">appcan天气</h1>
<div class="nav-btn" id="nav-right">
<!--按钮开始-->
<!--按钮结束-->
</div>
</div>
<!--header结束-->
```
删除默认的背景图片，你也可也在css中修改，index/css/main.css

2）、 打开index_content.html页面这个是我们的内容页面。因为这是天气列表内容页，引入列表控件的js文件、css文件（appcan.listview.js、appcan.control.css）,在body中插入一个容器元素来显示列表内容。
```
<div class="city-list content">
</div>
```
3）、用listview控件添加列表内容我们添加六个城市，listview的icon我们放置天气状况，设置天气列表,刚开始我们我们用默认图片，等列表加载完成之后我们 用appcan.request.ajax()方法异步请求真正的天气列表数据。
  ```
var lv = appcan.listview({
            selector : ".city-list",
            hasIcon : true,
            hasAngle : true
        });
 
        lv.set([{
            title : "北京",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        }, {
 
            title : "南京",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        }, {
 
            title : "杭州",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },{
 
            title : "深圳",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },{
 
            title : "上海",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },{
 
            title : "三亚",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },{
 
            title : "昆明",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        }]);
```
列表添加完成，异步获取天气状况，我们用百度的天气api。
```
function updateInfo(city,ele){
varweatherUrl = 'http://api.map.baidu.com/telematics/v3/weather?location='+city+'&output=json&ak=hTXrtTGGcljoOMdf2jZcc1yD';
appcan.request.ajax({
url:weatherUrl,
type:'GET',
dataType:"json",
success: function(data){
if(data.error){
                    alert('获取天气出错');
}else{
varweatherData = data.results[0].weather_data;
var today = weatherData[0];
                   $(ele).find('.lis-icon-s').css('background-image','url("'+today.dayPictureUrl+'")');
                }
            }
        });
}
```
 添加点击事件，当点击的时候保存点击的城市，并打开详情页面。
 ```
function openDetail(city){
            appcan.window.open({ name:'detail',
                data:'detail.html?'+city,
                aniId:10
            });
            appcan.locStorage.val('city',city);
        }
        lv.on('click', function(ele, obj, subobj) {
            openDetail(encodeURI(obj.title));
        });
```
4）、我们添加一个方法当页面下拉的时候完成刷新动作，appcan sdk中已经封装好了该方法
  ```
function openDetail(city){
         appcan.frame.setBounce(0, function(type) {
        }, function(type) {
        }, function(type) {
            $('.city-list li').each(function(i,v){
                var data = v.lv_data;
                if(!data){
                    return;
                }
                updateInfo(encodeURI(data.title),v);
            });
            appcan.frame.resetBounce(type);
        })
```
5）、到此我们就完成了整个城市列表的内容了下面就是完成的内容。
  ```
<!DOCTYPE html>
<html class="um landscape min-width-240px min-width-320px min-width-480px min-width-768px min-width-1024px">
<head>
<title></title>
<meta charset="utf-8">
<meta name="viewport" content="target-densitydpi=device-dpi, width=device-width, initial-scale=1, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
<link rel="stylesheet" href="css/fonts/font-awesome.min.css">
<link rel="stylesheet" href="css/ui-base.css">
<link rel="stylesheet" href="css/ui-box.css">
<link rel="stylesheet" href="index/css/main.css">
<link rel="stylesheet" href="css/ui-color.css">
<link rel="stylesheet" href="css/appcan.control.css">
</head>
<body class="um-vp" ontouchstart>
<div class="city-list content">
</div>
<script src="js/appcan.js"></script>
<script src="js/plugin/appcan_plugin.js"></script>
<script src="js/appcan.listview.js"></script>
<script>
 
    function updateInfo(city,ele){
        var weatherUrl = 'http://api.map.baidu.com/telematics/v3/weather?location='+city+'&output=json&ak=hTXrtTGGcljoOMdf2jZcc1yD';
        appcan.request.getJSON(weatherUrl,function(data){
           if(data.error){
                alert('获取天气出错');
            }else{
                var weatherData = data.results[0].weather_data;
                var today = weatherData[0];
                $(ele).find('.lis-icon-s').css('background-image','url("'+today.dayPictureUrl+'")');
            }
 
        });
 
    }
    appcan.ready(function(){
        appcan.frame.setBounce(0, function(type) {
           //$("#pullstatus"+type).html(!type?"开始下拉":"开始上拖");
        }, function(type) {
            //$("#pullstatus"+type).html(!type?"下拉超过临界点,产生事件了！":"超过临界点,产生事件了！");
        }, function(type) {
            $('.city-list li').each(function(i,v){
                var data = v.lv_data;
                if(!data){
                    return;
                }
                updateInfo(encodeURI(data.title),v);
            });
            appcan.frame.resetBounce(type);
        })
 
 
        var lv = appcan.listview({
            selector : ".city-list",
            hasIcon : true,
            hasAngle : true
        });
 
 
        lv.set([{
            title : "北京",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        }, 
		{
            title : "南京",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },
		{
 
            title : "杭州", 
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },
		{
 
            title : "深圳",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
 
        },
		{
 
            title : "上海",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },
		{
            title : "三亚",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        },
		{
            title : "昆明",
            icon:"./css/res/appcan_s.png",
            icontitle : "",
        }]);
 
 
        function openDetail(city){
            appcan.window.open({
                name:'detail',
                data:'detail.html?'+city,
                aniId:10
            });
            appcan.locStorage.val('city',city);
        }
        lv.on('click', function(ele, obj, subobj) {
            openDetail(encodeURI(obj.title));
        });
 
 
        $('.city-list li').each(function(i,v){
            var data = v.lv_data;
            if(!data){
                return;
            }
            updateInfo(encodeURI(data.title),v);
        });
    })
</script>
</body>
</html>
```
6）、新增天气详情页面detail.html、detail_content.html两个页面detail.html页面里面我们加一个标题和页尾，标题加一个返回按钮
   ```
<!--header开始-->
<div id="header" class="uh t-wh ub c-blu">
<!- 返回按钮开始 -->
<div class="nav-btn" id="nav-left">
<div class="fa fa-arrow-left ulev2"></div>
</div>
<!- 返回按钮结束 -->
<h1 class="ut ub-f1 ulev-3 ut-s tx-c" tabindex="0">
<span class="detail-title"></span>
</h1>
 
<div class="nav-btn umw4 ub ub-ac ub-pc">
                 
</div>
</div>
<!--header结束--><!--content开始-->
<div id="content" class="ub-f1 tx-l appCan ub-img4">
 
 
</div>
<!--content结束-->
<!--footer-->
<div id="footer" class="uinn-z1">
<div class="tx-c t-93 ulev0 ufm1">www.appcan.cn</div>
<div class="tx-c t-93 ulev-4 umar-at1">正益无线（北京）科技有限公司</div>
</div>
```
7）、我们用button控件来给返回按钮加上事件
  ```
 appcan.button(".nav-btn", "btn-act", function() {
            appcan.window.close(-1);
        });
```
8）、获取当前城市并设置当前状态页面，标题的内容
```
var city = appcan.locStorage.val('city');
         $('.detail-title').html(decodeURI(city)+'天气详情');
```
9）、现在添加城市天气详情页面，因为天气为三天的天气，所以我们这里可以用列表控件，先生成列表数据，三天天气都大致相同，我们定义一个模版。
 ```
<script type="text/template" id="weather-tmp">
 
<div class="day">
<span class="temperature"><%-weather_data.temperature%></span>
<div>
<span><%-weather_data.wind%></span>
<span><%-weather_data.weather%></span>
</div>
<span class="weather-pic">
<img src="<%-weather_data.dayPictureUrl%>"><br>
<span><%-weather_data.date%></span>
</span>
</div>
 
</script>
```
10）、新增更新天气函数，来更新天气数据
```
function updateForecast(weatherData){
		//生成列表模版
        var render = appcan.view.template($('#weather-tmp').html());
        var weatherList =[];
        		//遍历整个数据渲染整个列表添加到数据中
                for(var i =0,len=weatherData.length;i<len;i++){
            var res = render({weather_data:weatherData[i]});
            weatherList.push({
                title:res
            });
        }
        		//创建一个listview对象设置渲染的数据到列表中
		        var lv = appcan.listview({
            selector : ".city-detail",
            hasIcon : false,
            hasAngle : false
        });
        lv.set(weatherList);
            }
```
11）、执行更新数据，在更新数据前先打开一个提示框表明正在加载数据，当数据加载成功删除提示框，把获取的数据传给更新列表函数进行渲染
 ```
function updateInfo(city){
      
 
/打开一个没有弹出框的toast
        appcan.window.openToast({
            msg:'加载天气数据...',
            duration:0,
            position:5,
            type:0
        });
varweatherUrl = 'http://api.map.baidu.com/telematics/v3/weather?location='+city+'&output=json&ak=hTXrtTGGcljoOMdf2jZcc1yD';
appcan.request.ajax({
           url:weatherUrl,
type:'GET',
dataType:"json",
           success: function(data){
                if(data.error){
                    alert('获取天气出错');
                }else{
varweatherData = data.results[0].weather_data;
var today = weatherData[0];
updateForecast(weatherData);
                }
appcan.window.closeToast();
           }
        });
  }
  12）初始化页面，获取传来的城市然后根据该城市更新页面数据
    appcan.ready(function(){
        appcan.initBounce();
        var city = appcan.locStorage.val('city');
        updateInfo(city);
 
    })
```
###4、应用打包
  开发完成打包应用有两种方式，一种是本地打包，一种是线上打包。
####4.1、本地打包
1）、点击发行
 ![](http://newdocx.appcan.cn/docximg/180435r2014p9g22f.jpg) 

或者右键点击phone，然后点击生成安装包
 ![](http://newdocx.appcan.cn/docximg/180445y2014g9s22l.jpg) 
 
2）、可以修改应用名称，上传图标，我们使用默认的然后点击下一步
 ![](http://newdocx.appcan.cn/docximg/180451l2014m9l22x.jpg) 
 
3）、选择要生成的平台，启动画面点击下一步
 ![](http://newdocx.appcan.cn/docximg/180501v2014o9g22w.jpg) 
 
4）、选择需要的插件然后点击完成。等待打包如果打包完成就会自动打开应用目录。
 ![](http://newdocx.appcan.cn/docximg/180512p2014s9z22t.jpg) 
  
####4.2、线上打包
1）、点击右键把代码提交的服务器 
 ![](http://newdocx.appcan.cn/docximg/180523b2014q9b22f.jpg) 
  
2）、选择要提交的文件。点击ok
 ![](http://newdocx.appcan.cn/docximg/180533r2014z9b22m.jpg) 
 
3）、选择应用进入详情页面，并点击应用开发，进入应用开发页面
 ![](http://newdocx.appcan.cn/docximg/180544i2014c9x22a.jpg) 
 
4）、点击应用打包，点击图标设置可以修改图标，点击启动页面可以修改启动页面，然后选择插件，证书，最后点击远端打包。
 ![](http://newdocx.appcan.cn/docximg/180748s2014r9y22g.jpg) 
 
5）、选择平台和版本号，点击生成安装包。
 ![](http://newdocx.appcan.cn/docximg/180804h2014t9k22i.jpg) 
 
6）、等待打包完成，可以下载生成的安装包了，下一步就进入应用管理页面了。
  ![](http://newdocx.appcan.cn/docximg/164638g2014v9y23i.jpg) 
  
   ![](http://newdocx.appcan.cn/docximg/180816y2014t9s22q.jpg) 


