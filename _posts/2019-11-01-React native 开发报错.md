---
layout:     post
title:      React native 开发报错
subtitle:   React native 开发报错
date:       2019-11-01
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - Blog
---

# React native 开发报错

## 1. 使用 react-native-swiper 报错
[react-native-swiper  地址](https://github.com/leecade/react-native-swiper)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019110119092490.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
这是react-native-swiper 版本 错误
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191101191210324.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
使用这个 ==npm i --save react-native-swiper@nightly==




## 2. [react-native-scrollable-tab-view](https://github.com/ptomasroos/react-native-scrollable-tab-view) 使用 报错

[案例](https://www.jianshu.com/p/2e50cf60ac97)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113114101342.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

==解决方法==

     yarn add @react-native-community/viewpager
     react-native link @react-native-community/viewpager
     并重建和解决它

## 3.使用TouchableHighlight  报错
[TouchableHighlight 使用](https://reactnative.cn/docs/touchablehighlight/)
[TouchableOpacity 使用](https://reactnative.cn/docs/touchableopacity/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113114630463.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

意思是 < TouchableHighlight > < /TouchableHighlight> 中 必须有且只能有一个 < View></ View>

解决方案  
     1. 修改TouchableHighlight中的子级 
     2.使用 TouchableOpacity ，可以允许同时存在几个子级  
       < TouchableOpacity>< View></ View> < Text> </ Text></ TouchableOpacity>    

## 4.使用< Text> 报错

   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113175614346.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

## 5.运行报错 No bundle URL present

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191113175632228.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
关闭模拟器,完全对退出模拟器
重新运行 react-native run-android   / react-native run-ios


## 6.运行报错 WebView has been removed from React Native
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191127092931513.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
意思： 不变冲突:WebView已从React Native中移除。它现在可以安装和导入从'react-native webview'而不是'react-native'。看到https://github.com/react-native-community react-native-webview

其实是引用 native-echarts 报错

## 7.ECharts 引用不显示解决

1./node_modules/native-echarts/src/components/Echarts/ 目录下的tpl.html 拷贝一份 
2./android／app/src/main 创建 assets文件夹
3.把第一步拷贝的文件放到第二步创建的assets文件夹下
4.进入Echarts文件(/node_modules/native-echarts/src/components/Echarts/index) 把WebView的source改为

    import { WebView, View, StyleSheet, Platform } from 'react-native';
    改成 
    import { View, StyleSheet, Platform } from 'react-native';
    import { WebView } from 'react-native-webview';
    
    source={{uri: 'file:///android_asset/tpl.html'}}


## 8.真机测试 调用github项目图片 无法显示 Android 9.0网络权限适配

解释：在做Android开发时，使用华为的p20和平板（均为Android 9.0）测试时，发现不能使用WIFI网络

react native项目中 

android -> app -> src -> main  -> 
res  ->新建文件夹 名（ xml ）  > 新建文件 ( network-security.config.xml )
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129143947821.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129144015559.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

		<?xml version="1.0" encoding="utf-8"?>
		<network-security-config>
		   <base-config cleartextTrafficPermitted="true">
		       <trust-anchors>
		           <certificates src="system" overridePins="true" />
		           <certificates src="user" overridePins="true" />
		       </trust-anchors>
		   </base-config>
		</network-security-config>

在==AndroidManifest.xml==清单文件上加入

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129144426399.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
       
       android:networkSecurityConfig="@xml/network_security_config"

## 9. Error: 'createNavigationContainer() has been removed.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191129144657848.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
		
		问题
		Error: 'createNavigationContainer() has been removed. Use 'createAppContainer() instead. 
		You can also import createAppContainer directly from @react-navigation/native
		This error is located at: 
		 in Router (at Main.js:29) 
		 in Main (at renderApplication.js:40) 
		 in RCTView (at AppContainer.js:101) 
		 in RCTView (at AppContainer.js:119) 
		 in AppContainer (at renderApplication.js: 39)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191202193150680.png)
解决
[github 网址](https://github.com/aksonov/react-native-router-flux/issues/3571)
      

    npm install  react-native-router-flux@v4.2.0-beta.x  例如（npm install  react-native-router-flux@v4.2.0-beta.1）