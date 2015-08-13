AppCan IDE为开发者提供了应用加密功能，支持全包（.html文件、.css文件、.js文件）加密及部分（可选文件）加密，以保证您的代码安全。
>温馨提示：使用AppCan提供的在线加密功能，需要加密的文件统一为uft-8编码，注意````<head>元素内部<meta>````标签定义的字符编码要与原html保存的编码统一为uft-8（使用加密）

在IDE中应用开发完成后，修改config.xml文件，默认为全包加密。
![](http://newdocx.appcan.cn/docximg/110303h2015p0w31o.jpg)

若勾选“部分加密”，则显示当前应用下的目录结构（css目录、js目录及html文件）。
![](http://newdocx.appcan.cn/docximg/110359g2015q0m31g.jpg)

选择全部或部分加密后，保存config.xml文件（注：首先关闭上图的弹出框，手动Ctrl+s保存config.xml文件，再次点击部分加密选项按钮，选择你要加密的文件），这时在当前应用目录下会自动生成一个obfuscation.xml文件，里面存放了被加密的文件名。
![](http://newdocx.appcan.cn/docximg/110632d2015l0p31c.jpg)

提交代码至线上，在官网生成安装包，代码即被加密，解压安装包后可见代码文件为乱码 。
![](http://newdocx.appcan.cn/docximg/112649t2015g0e31g.jpg)
