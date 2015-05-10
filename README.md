kbengine_unity3d_warring
=============

##本项目作为KBEngine服务端引擎的客户端演示而写，适用于Unity4.x
http://www.kbengine.org

##官方论坛

	http://bbs.kbengine.org


##QQ交流群

	16535321 


##GO!

	1. 确保已经下载过KBEngine服务端引擎，如果没有下载请先下载
		下载服务端源码(KBEngine)：
			https://github.com/kbengine/kbengine/releases/latest

		编译(KBEngine)：
			http://www.kbengine.org/docs/build.html

		安装(KBEngine)：
			http://www.kbengine.org/docs/installation.html

	2. 下载KBEngine客户端插件与服务端Demo资产库:

		* 使用git命令行，进入到kbengine_unity3d_warring目录执行：

			git submodule update --init --remote
![submodule_update1](http://www.kbengine.org/assets/img/screenshots/gitbash_submodule.png)

		* 或者使用 TortoiseGit(选择菜单): TortoiseGit -> Submodule Update:
![submodule_update2](http://www.kbengine.org/assets/img/screenshots/unity3d_plugins_submodule_update.jpg)

                * 也可以手动下载kbengine客户端插件与服务端Demo资产库

		        客户端插件下载：
		            https://github.com/kbengine/kbengine_unity3d_plugins/releases/latest
		            下载后请将其解压缩，插件源码请放置在: Assets/plugins/kbengine/kbengine_unity3d_plugins

		        服务端资产库下载：
		            https://github.com/kbengine/kbengine_demos_assets/releases/latest
		            下载后请将其解压缩,并将目录文件放置于服务端引擎根目录"kbengine/"之下，如下图：

	3. 拷贝服务端资产库"kbengine_demos_assets"到服务端引擎根目录"kbengine/"之下，如下图：
![demo_configure](http://www.kbengine.org/assets/img/screenshots/demo_copy_kbengine.jpg)


##配置Demo(可选):

	创建AssetBundles(默认已经创建，可以跳过这一步)：
		unity3d(菜单上)->Publish->Build Publish AssetBundles(打包所有需要动态加载资源)

		期间可能一直出现"Moving file failed"， 需要点击"try again"让其继续, 
		这可能是unity3d在移动文件时文件被占用造成的。
		执行完毕后检查 Assets->StreamingAssets是否有内容。

	生成服务端寻路数据(默认已经创建，可以跳过这一步)：
		先将Assets\Plugins\cai-nmgen-rcn(generate navmesh).zip解压放当前目录下并重启unity3d编辑器, 然后执行如下步骤:
			unity3d资源浏览器中选中(非菜单): Assets->Nav_build->xinshoucun->NavmeshBuild->Build & Bake, 等待生成完成之后
			unity3d资源浏览器中选中(非菜单): Assets->Nav_build->xinshoucun->CAIBakedNavmesh->Save, 将其中srv_xxx.navmesh放到服务端kbengine\kbengine_demos_assets\res\spaces\xinshoucun中
		(注意: 生成完毕后建议删除cai-nmgen-rcn(generate navmesh).zip解压出来的文件，会造成无法导出游戏的错误，原因未知。)
		(如果有更多问题请咨询插件作者: http://www.critterai.org/projects/cainav/)

	改变登录IP地址与端口（注意：关于服务端端口部分参看http://www.kbengine.org/cn/docs/installation.html）:
![demo_configure](http://www.kbengine.org/assets/img/screenshots/demo_configure.jpg)

		kbengine_unity3d_warring\Scripts\kbe_scripts\clientapp.cs -> ip
		kbengine_unity3d_warring\Scripts\kbe_scripts\clientapp.cs -> port

##启动服务器:

	先开启服务端
		Windows:
			kbengine\kbengine_demos_assets\start_server.bat

		Linux:
			kbengine\kbengine_demos_assets\start_server.sh

	检查启动状态:
		如果启动成功将会在日志中找到"Components::process(): Found all the components!"。
		任何其他情况请在日志中搜索"ERROR"关键字，根据错误描述尝试解决。
		(More: http://www.kbengine.org/cn/docs/startup_shutdown.html)

##导出WebPlayer项目:

	Unity3d File->Build Settings->Scenes In Build选择scenes/start.unity->Platform
	选择Web Player->Build。 


##在Unity3D编辑器运行游戏
	
	Unity3D中选择Assets\scenes\start场景然后点击编辑器运行按钮，如果无意外应该可以登录游戏进入到场景中了。
	(注意：运行游戏前请确保Unity3D控制台“错误暂停”是取消状态，因为一些原因一定会遇到错误，参考：http://bbs.kbengine.org/forum.php?mod=viewthread&tid=20&extra=page%3D1)

![unity_error_pause](http://www.kbengine.org/assets/img/screenshots/unity_error_pause.png)


##在浏览器运行游戏:

	Web服务器部署文件夹结构:

		->(服务器根目录)
			- StreamingAssets (创建AssetBundles生成的文件夹)
			- ui (Assets下的ui文件夹可以直接拷贝过来)
			- crossdomain.xml
			- initLogo.png
			- initProgressBar.PNG
			- initProgressFrame.PNG
			- index.html
			- Unity3d.unity3d (在unity3d编译时生成的文件)
			- Unity3d.html (在unity3d编译时生成的文件)


	浏览器访问localhost
	如不清楚请下载编译打包好的demo，并按照其中的文件夹结构放置并看压缩包内文档教程如何启动:
	https://sourceforge.net/projects/kbengine/files/


##WebPlayer日志:

	Windows XP: C:\Documents and Settings\username\Local  Settings\Temp\UnityWebPlayer\log
	Windows Vista/7: C:\Users\username\AppData\Local\Temp\UnityWebPlayer\log

##warring截图
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo1.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo2.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo3.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo4.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo5.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo6.jpg)
![warring项目运行效果](http://www.kbengine.org/assets/img/screenshots/unity3d_demo33.jpg)
