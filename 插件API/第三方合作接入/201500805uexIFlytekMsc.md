[TOC]
#1、简介

科大讯飞语音插件
##1.1、 业务限制资源规格限制说明
科大讯飞语音插件是基于讯飞语音云API封装集成到AppCan平台的第三方api模块， 用 户 可以使用本插件实现基本的的语音服务。目前本插件仅支持在线语音听写和 在线语 音合成。
> 温馨提示：uexIFlytekMsc插件分别封装speechUtility、speechRecognizer、 speechSynthesizer3个类，因此插件调用的时候需要区分这3个类别名，注意每个 方 法的正确写法。

##1.2、UI展示
 ![](http://newdocx.appcan.cn/docxapi/)
 ![](http://newdocx.appcan.cn/docxapi/)
##1.3、申请开通
[申请开通](http://newdocx.appcan.cn/newdocx/docx?type=1282_1278)立即使用
 > 自定义插件使用，需要提前申请
 
 
##1.4 、术语表

Path Types

|  协议头 |  Android对应路径 (其中"/sdcard/"等 同于"/storage/emulated/0/") | iOS对应路径  |
| ------------ | ------------ | ------------ |
| res:// |widget/wgtRes/   |widget/wgtRes   |
|  wgts:// | /storage/emulated/0/widgetone/apps/ xxx(widgetAppId)/  |  /Documents/apps/xxx(widgetAppId)/ |
|  wgts:// |  /storage/emulated/0/widgetone/widgets/ |  /Documents/widgets/ |
|  file:///sdcard/ | /storage/emulated/0/  | 无  |
#2、API概览 
##2.1、方法

> ### 			createUtility  		初始化客户端引擎选择模式

`speechUtility.createUtility(params);		`			
**		说明:		**	
初始化即创建语音配置对象，只有初始化后才可以使用MSC的各项服务。					
**		参数:		**	
````
 params: (String类型) 必选 初始化参数 var params = "engine_mode=msc,appid=12345678"
 ````
 各字段含义如下：
 
|						appid					|						engine_mode					|
|-----|-----|
|						语音应用ID（初始化字段）（必填）<br>//将“12345678”替换成您申请的APPID，<br>申请开通：<spanstyle="color:#E56600;">应用管理第三方API功能</span>即可获取，<a href="http://newdocx.appcan.cn/newdocx/docx?type=978_975"target="_blank"><spanstyle="color:#337FE5;">详细操作见</span></a>					|						初始化客户端引擎选择模式（选填）<br>可选：msc（只使用MSC），plus（只使用语音+），<br>auto（云端优先使用MSC，本地优先使用语音+）默认：auto					|
**	平台支持:		**	
Android2.2+					

**	版本支持：		**	
3.0.0+					
**		示例:		**	

```
 					var params = "engine_mode=msc,appid=12345678"或者
					// 将“12345678”替换成您申请的APPID， 
window.uexOnload = function() {
	speechUtility.createUtility("engine_mode=msc,appid=12345678");
}

				
```
> ### 		createRecognizer  	创建听写示例对象,多次调用不会重复初始化	

`speechRecognizer.createRecognizer();			`
**		说明:	**	
创建听写示例对象,多次调用不会重复初始化			
**	参数:	**	
无			
**		平台支持:	**	
Android2.2+			
					  			
**	版本支持：	**	
3.0.0+			
**		示例:	**	

```
 
		  <!DOCTYPE HTML>
<html>
<head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="viewport"
	content="width=device-width, initial-scale=1, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
	<link rel="stylesheet" type="text/css" href="css/index.css">
	
	<script type="text/javascript">
	function onInit(opCode, dataType, data){
		document.getElementById('error').value = "错误信息:" + data;
	}
	
	function onVolumeChanged(opCode, dataType, data){
		document.getElementById('volume').value = "音量回调:" + data;
	}
	
	function onResult(opCode, dataType, data){
		document.getElementById('result').innerHTML = "以下是识别结果：<br>" + data;
	}
	
	function onError(opCode, dataType, data){
		document.getElementById('error').value = "错误信息:" + data;
	}
	
	function onBeginOfSpeech(opCode, dataType, data){
		document.getElementById('begin').value = "开始语音输入true";
	}
	
	function onEndOfSpeech(opCode, dataType, data){
		document.getElementById('end').value = "结束语音输入true";
	}
	
	<!-- 注册回调 -->
	window.uexOnload = function(type){
		speechRecognizer.onInitJs = onInit;
		speechRecognizer.onVolumeChangedJs = onVolumeChanged;
		speechRecognizer.onResultJs = onResult;
		speechRecognizer.onErrorJs = onError;
		speechRecognizer.onBeginOfSpeechJs = onBeginOfSpeech;
		speechRecognizer.onEndOfSpeechJs = onEndOfSpeech;
		// 启动时初始化识别对象
		speechRecognizer.createRecognizer();
	}
	
	<!-- 开始语音听写 -->
	function start(){
		clear();
		// 设置听写引擎
		speechRecognizer.setParameter("engine_type", "cloud");
		// 设置返回结果格式
		speechRecognizer.setParameter("result_type", "json");
		// 设置语言
		speechRecognizer.setParameter("language", "zh_cn");
		// 设置语言区域
		speechRecognizer.setParameter("accent","mandarin");
		// 设置语音前端点
		speechRecognizer.setParameter("vad_bos", "4000");
		// 设置语音后端点
		speechRecognizer.setParameter("vad_eos", "1000");
		// 设置标点符号
		speechRecognizer.setParameter("asr_ptt", "1");
		// 启动识别
		speechRecognizer.startListening();
	}
	
	<!-- 清除界面内容 -->
	function clear(){
		document.getElementById('volume').value = "音量回调:";
		document.getElementById('result').innerHTML = "以下是识别结果：<br>" ;
		document.getElementById('error').value = "错误信息:";
		document.getElementById('begin').value = "开始语音输入false";
		document.getElementById('end').value = "结束语音输入false";
	}
	
	
</script>
</head>

<body>
	<div class="tit">讯飞语音对象</div>
	<div class="conbor">
		<div class="consj">
			<span>1.讯飞语音听写接口</span>
			<input class="btn" type="button" value="点击调用接口" onclick="start();"><br><br>
			<div class="tcxx" id="result">
			此接口将开启一次语音听写，将您读出的语音转换成文字。
			</div>
			<input class="textbox" type="text" id="volume" value="音量回调:">
			<input class="textbox" type="text" id="begin" value="开始语音输入false">
			<input class="textbox" type="text" id="end" value="结束语音输入false">
			<input class="textbox" type="text" id="error" value="错误信息:">
		</div>
	</div>
</body>
</html>

			
```
> ### 		setParameter	设置听写参数，参用键-值对的方法传入数据，请在启动语音识别前传入

` speechRecognizer.setParameter(key,value);			`
**	说明:	**	
设置听写参数，参用键-值对的方法传入数据，请至开始语音识别时传入			
**	参数:	**	
````
	  key:(String类型) 必填可选 传入的键  
	  value:(string类型)必填可选 传入的键对应的值  			
````

|   |   |   |   |   |   |   |   |   |   |   |   |   |   |
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------|------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| **key 字段 ** |  engi ne_ty pe |acce nt   | asr_au dio_p ath  | asr_dwa  | asr_ptt  |  domain |  reque st_ audio _focus | speec h_time out |  langu age |  timeout |  result_ type |  vad_bos | vad_eos  |
|  **说明** |  设置 识别 引擎 |  识别 语言 区域 |  识别 录音 保存 路径 |  设置识 别结果 是否结 果动态 修正 | 设置识 别结果 是否有 标点符 号  |  识别应 用领域| 设置是 否会话 过程中 暂停后 台音乐 播放  |  语音输 入超时 时间 |   识别 语言|  网络连 接超时 时间 |听写 返回 结果 类型   |VAD前 端点超 时  | VAD后 端点超 时  |
| **value 值**  | 在线: cloud， 离线： local， 暂支持 cloud  | 可选： man darin (普通 话)， canto nese (粤语)  |  路径 协议 详见  <a href="http://newdocx.appcan.cn/index.htmltemplateId=301"target="_blank">cons</a> <a href="http://newdocx.appcan.cn/newdocx/ejsTemplate?type=978_975"target="_blank">tant</a> 的Path  Types 注：  如 需保 存到 SD CARD，  需添  加 WRITE_ EXTER NAL_ST ORAGE 的权限 |  可选值： 0（否）， 1（是）  默认值： 0 |   可选值： 0（无） 1（有）  默认值： 0| 识别： iat， search， video， poi， music  | 外部不 需要暂 停后台 音乐播 放，需 设置为  false， 默认 true  |单位： ms， 默认 60000   | 支持： zh_cn， zh_tw， en_us  | 单位： ms， 默认 20000  | 可选： xml， json  默认： json  |  可选范 围：10 00 -10000 (单位 ms) 默认 值：短信 转写 5000， 其他 4000 |  可选范 围：0- 10000 (单位ms)  默认值： 短信转 写1800 ，其他 700 |
 
**		平台支持:	**	
Android2.2+			
					  			
**		版本支持：	**	
3.0.0+			
**		示例:	**	
见createRecognizer	
> ### 		startListening  	开始语音识别，启动录音，该接口无需参入参数。	

`speechRecognizer.startListening();		`
**		说明:		**	
开始语音识别，启动录音，该接口无需参入参数。					
**		参数:		**	
无					
**		平台支持:		**	
Android2.2+					
							  					
**			版本支持：		**	
3.0.0+					
**		示例:		**	
见createRecognizer		
> ### 			stopListening  		关闭录音，等待识别结果，该接口无需参入参数。		

`speechRecognizer.stopListening();					`
**	说明:		**	
关闭录音，等待识别结果，该接口无需参入参数。					
**		平台支持:		**	
Android2.2+					
							  					
**		版本支持：		**	
3.0.0+					
**		示例:		**	
见createRecognizer		
> ### 			cancel  		取消识别,调用该接口不会有结果返回		

`speechRecognizer.cancel();					`
**		说明:		**	
取消识别,调用该接口不会有结果返回					
**		参数:		**	
无		
**			平台支持:		**	
Android2.2+					
							  					
**			版本支持：		**	
3.0.0+					
**		示例:		**	
见createRecognizer		
> ### 			createSynthesizer  		创建合成对象，多次调用不会重复初始化		

`speechSynthesizer.createSynthesizer();					`
**			说明:		**	
创建合成对象，多次调用不会重复初始化					
**		参数:		**	
无		
**		平台支持:		**	
Android2.2+					

**		版本支持：		**	
3.0.0+					
**			 示例:		**	

```
 
		   <!DOCTYPE HTML>
<html>
<head>
   <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="viewport"
	content="width=device-width, initial-scale=1, user-scalable=no, minimum-scale=1.0, maximum-scale=1.0">
	<link rel="stylesheet" type="text/css" href="css/index.css">
	
	<script type="text/javascript">
	//开始合成
	function onSpeakBegin(opCode, dataType, data) {
		document.getElementById('state').value = "合成状态：开始";
		document.getElementById('error').value = "完成信息：";
	}
	//暂停合成
	function onSpeakPaused(opCode, dataType, data){
		document.getElementById('state').value = "合成状态：暂停";
	}
	//恢复合成
	function onSpeakResumed(opCode, dataType, data){
		document.getElementById('state').value = "合成状态：恢复";
	}
	//合成完成（包含错误信息）
	function onCompleted(opCode, dataType, data){
		document.getElementById('error').value = "完成信息："+data;
		document.getElementById('buffer').value = "缓冲进度回调:null";
		document.getElementById('play').value = "播放进度回调:null";
		document.getElementById('state').value = "合成状态：" + data;
	}
	//合成进度
	function onSpeakProgress(opCode, dataType, data) {
		document.getElementById('play').value = "播放进度回调:" + data;
	}
	//缓冲进度
	function onBufferProgress(opCode, dataType, data) {
		document.getElementById('buffer').value = "缓冲进度回调:" + data;
	}
	//初始化
	function onInit(opCode, dataType, data) {
		document.getElementById('error').value = "完成信息:" + data;
	}
	
	<!-- 注册回调 -->
	window.uexOnload = function(type){
		speechSynthesizer.onInitJs = onInit;
		speechSynthesizer.onSpeakResumedJs = onSpeakResumed;
		speechSynthesizer.onSpeakProgressJs = onSpeakProgress;
		speechSynthesizer.onSpeakPausedJs = onSpeakPaused;
		speechSynthesizer.onSpeakBeginJs = onSpeakBegin;
		speechSynthesizer.onCompletedJs = onCompleted; 
		speechSynthesizer.onBufferProgressJs = onBufferProgress;
		// 初始化合成对象
		speechSynthesizer.createSynthesizer();
	}
	
	<!-- 开始语音听写 -->
	function start(){
		clear();
		var text = document.getElementById('ttstext').value;
		
		//设置在线
		speechSynthesizer.setParameter("engine_type","cloud");
		//设置发音人
		speechSynthesizer.setParameter("voice_name","xiaoyan");
		//设置语速
		speechSynthesizer.setParameter("speed","50");
		//设置音调
		speechSynthesizer.setParameter("pitch","50");
		//设置音量
		speechSynthesizer.setParameter("volume","50");
		//设置播放器音频流类型
		speechSynthesizer.setParameter("stream_type","3");
		
		speechSynthesizer.startSpeaking(text);
	}
	
	function pause(){
		speechSynthesizer.pauseSpeaking();
        document.getElementById('state').value = "合成状态：暂停";
	}
	
	function resume(){
		speechSynthesizer.resumeSpeaking();
		document.getElementById('state').value = "合成状态：恢复";
	}
	
	function stop(){
		speechSynthesizer.stopSpeaking();
		document.getElementById('state').value = "合成状态：取消";
	}
	
	<!-- 清除界面内容 -->
	function clear(){
		document.getElementById('state').value = "合成状态：无";
		document.getElementById('buffer').value = "缓冲进度回调:null";
		document.getElementById('play').value = "播放进度回调:null";
		document.getElementById('error').value = "完成信息:";
	}
	
</script>
</head>

<body>
	<div class="tit">讯飞合成对象</div>
	<div class="conbor">
		<div class="consj">
			<span>2.讯飞语音合成接口</span>
			<input class="btn" type="button" value="开始合成" onclick="start();">
			<input class="btn" type="button" value="暂停合成" onclick="pause();">
			<input class="btn" type="button" value="继续合成" onclick="resume();">
			<input class="btn" type="button" value="取消合成" onclick="stop();">
			<div class="tcxx" id="result">
				<TextArea class="textbox" type="text" id="ttstext" style="height：'40px',width='100%'"  >科大讯飞作为中国最大的智能语音技术提供商!
				
```
> ### 			setParameter		设置听写参数 

`speechSynthesizer.setParameter(key,value);					`
**		说明:		**	
设置听写参数，参用键-值对的方法传入数据，请在启动语音合成前传入					
**			参数:		**	
````
	  key:(String类型) 必填可选 传入的键
	  value:(string类型) 必填可选传入的键对应的值  					
````

|   |   |   |   |   |   |   |   |   |   |   |   |   |   
| ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ | ------------ |
| **key 字段 ** |  engi ne_ty pe |backg round_ sound  | voice_ name| speed  | pitch  |  volu me |  stream _type |  next_ text |  tts_ buffer _time |  sample _rate |  text |  tts_ audio _path |  
|  **说明** |  设置 识别 引擎 |  合成 背景 音乐 |  发音 人 | 合成 语速 | 音调  |  合成 音量| 播放 类型  |  需要 预合 成的 文本 内容|   播放 缓冲 时间， 即缓 冲多 少秒 音频 后开 始播 放|  合成 及识 别采 样率 |需要 合成 文本 内容   |合成 录音 保存 路径 |  
| **value 值**  | 在线: cloud， 离线： local， 暂支持 cloud  | 默认 值:无， 可选： 1  |  云端 支持 发音 人： 小燕 （xiao yan） 等等  对于 网络 TTS 的发 音人 角色， 不同 引擎 类型 支持 的发 音人 不同， 使用 中请 注意 选择。| 云端 支持： 0~ 100， 本地 支持： 0~ 200,  默认 值:50 |   （0~ 100） 默认 值:50| （0~ 100） 默认 值:50 | 参考 系统 Audio Manager 定义 ，如： Audio Manager .STREAM _MUSIC |文本 类型 0～ 1024 Byte | 如 tts_ buffer_ time =50 00  默认 缓冲 第一 句之 后播 放 | 可选 范围： 160 00， 8000  默认 值： 16000 | 文本 类型 0~ 1024 Byte  |  注： 如需 保存 到SD CAR D， 需添 加 WRI TE_ EXTE RNAL _STO RAGE 的权 限 |  

**	平台支持:		**	
Android2.2+					
							  					

**			版本支持：		**	
3.0.0+					
**			示例:		**	
			见createSynthesizer		
> ### 			startSpeaking  		开始合成		

`speechSynthesizer.startSpeaking(params);			`
**			说明:			**	
注：合成时，传入合成文本。							
**	 参数:			**	
````
	  params:(String类型) 必选传入合成文本  							
````
**			平台支持:			**	
Android2.2+							
									  							
**			版本支持：			**	
									  3.0.0+							
**		示例:			**	
				见createSynthesizer			
> ### 				pauseSpeaking  			暂停合成			

`speechSynthesizer.pauseSpeaking();		`					
**	说明:			**	
暂停合成							
**				平台支持:			**	
Android2.2+							
									  							
**		版本支持：			**	
3.0.0+							
**			示例:			**	
				见createSynthesizer			
> ### 				resumeSpeaking  			暂停后重新开始播放			

`speechSynthesizer.resumeSpeaking();		`					
**		说明:			**	
暂停后重新开始播放							
**		参数:			**	
				无			
**			平台支持:			**	
Android2.2+							

**		版本支持：			**	
3.0.0+							
**			示例:			**	
				见createSynthesizer			
> ### 				stopSpeaking  			停止合成，中止本次会话			

`speechSynthesizer.stopSpeaking();		`					
**		说明:			**	
									  停止合成，中止本次会话							
**		参数:			**	
				无			
**		平台支持:			**	
Android2.2+							
									  							
**		版本支持：			**	
									  3.0.0+							
**		示例:			**	
				见createSynthesizer			

##2.2、  	识别监听回调方法
> ### 				onInitJs  			识别对象初始化回调

`speechRecognizer.onInitJs(opId,dataType,data);`
**	说明:			**
识别对象初始化回调							
**		参数:			**
	 opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。		
	 dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型										  data:(String类型) 必选初始化信息							
**	版本支持：			**
3.0.0+							
**	示例:			**
				见createRecognizer			
> ### 				onVolumeChangedJs  			识别录音音量回调


`speechRecognizer.onVolumeChangedJs(opId,dataType,data);`
**			说明:			**	
识别录音音量回调							
**			参数:			**	
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(Int类型) 必选音量大小，返回值0~30
````
**		版本支持：			**
3.0.0+							
**		示例:			**
				见createRecognizer			
> ### 				onResultJs  			识别结果回调


`speechRecognizer.onResultJs(opId,dataType,data);`
**	说明:			**
识别结果回调							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选识别结果，一般是json类型
````
**	版本支持：			**
3.0.0+							
**		示例:			**
				见createRecognizer			
				
> ### 				onErrorJs  			识别错误回调


`speechRecognizer.onErrorJs(opId,dataType,data);`							
** 				说明:			**
识别错误回调							
**		参数:			**
````
	 opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	 dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型
	 data:(String类型) 必选识别错误回调信息
````
**版本支持：			**
3.0.0+							
**示例:			**
				见createRecognizer			
> ### 				onBeginOfSpeechJs  			 开始录音回调


`speechRecognizer.onBeginOfSpeechJs(opId,dataType,data);	`						
**	说明:			**
									  开始录音回调							
**	参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。			
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型
	  data:(String类型) 必选无数据返回							
````
**		版本支持：			**
3.0.0+							
**		示例:			**
				见createRecognizer			
> ### 				onEndOfSpeechJs  			结束录音回调


`speechRecognizer.onEndOfSpeechJs(opId,dataType,data);	`						
**	说明:			**
结束录音回调							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选无数据返回
````
**		版本支持：			**
3.0.0+							
**		示例:			**
				见createRecognizer			
##2.3、  	合成监听回调方法:
> ### 				onInitJs  			   合成对象初始化回调


`speechSynthesizer.onInitJs(opId,dataType,data);			`				
**		说明:			**
初始化回调							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选合成初始化信息							
````
**	版本支持：			**
									  3.0.0+							
**	示例:			**
				见createSynthesizer			
> ### 				onSpeakResumedJs  			恢复播放回调


`speechSynthesizer.onSpeakResumedJs(opId,dataType,data);			`				
**		说明:			**
恢复播放回调（调用resumeSpeaking方法无该回调）							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型
	  data:(String类型) 必选无数据返回
````
**	版本支持：			**
3.0.0+							
**	示例:			**
				见createSynthesizer			
> ### 				onSpeakProgressJs  			合成进度回调


` speechSynthesizer.onSpeakProgressJs(opId,dataType,data);`							
**		说明:			**
合成进度回调							
**			参数:		**	
````
	 opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	 dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选合成播放进度，0~100							
````
**	版本支持：			**
3.0.0+							
**示例:			**
				见createSynthesizer			
> ### 				onSpeakPausedJs  			暂停播放回调


`speechSynthesizer.onSpeakPausedJs(opId,dataType,data);			`				
**说明:			**
暂停播放回调（调用pauseSpeaking方法无该回调）							
**	参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。	
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型
	  data:(String类型) 必选无数据返回							
````
**	版本支持：			**
3.0.0+							
**	示例:			**
				见createSynthesizer			
> ### 				onSpeakBeginJs  			开始播放回调


`speechSynthesizer.onSpeakBeginJs(opId,dataType,data);			`				
**		说明:			**
开始播放回调							
**	参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型
	  data:(String类型) 必选无数据返回
````
**	版本支持：			**
3.0.0+							
**	示例:			**
				见createSynthesizer			
> ### 				onCompletedJs  			合成完成回调


`speechSynthesizer.onCompletedJs(opId,dataType,data);`							
**		说明:			**
合成完成回调							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选合成成功返回"Complete",合成失败返回错误信息
````

**	版本支持：			**
3.0.0+							
**		示例:			**
				见createSynthesizer			
> ### 				onBufferProgressJs  			合成缓冲回调


`speechSynthesizer.onBufferProgressJs(opId,dataType,data);	`						
**			说明:			**
合成缓冲回调							
**		参数:			**
````
	  opId:(Number类型) 必选操作ID，此函数中不起作用，可忽略。
	  dataType:(Number类型) 必选数据类型详见[CONSTANT]中Callback方法数据类型	
	  data:(String类型) 必选合成缓冲进度，0~100							
````
**		版本支持：			**
3.0.0+							
**	示例:			**
				见createSynthesizer			
  