---
layout:     post
title:      React native 及 Android 测试（真机  模拟器）
subtitle:   React native 及 Android 测试（真机  模拟器）
date:       2019-10-23
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - React-native
---

# React native 及  Android 测试（真机 / 模拟器）

##  react native 配置 
   [ react native 搭建开发环境](https://reactnative.cn/docs/getting-started/)

**安装依赖**
    必须安装的依赖有：Node、React Native 命令行工具、Python2 以及 JDK 和 Android Studio。

**Node, Python2, JDK**
     [Node  下载](http://nodejs.cn/)
     Python2
     [Java SE Development Kit (JDK) 下载](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   注意 Node 的版本必须大于等于 10，Python 的版本必须为 2.x（不支持 3.x），而 JDK 的版本必须是 1.8（目前不支持 1.9 及更高版本）。安装完 Node 后建议设置 npm 镜像（淘宝源）以加速后面的过程（或使用科学上网工具）。

   注意：不要使用 cnpm！cnpm 安装的模块路径比较奇怪，packager 不能正常识别！

	使用nrm工具切换淘宝源
	npx nrm use taobao
	
	如果之后需要切换回官方源可使用 
	npx nrm use npm


## Yarn、React Native 的命令行工具（react-native-cli）

   Yarn是 Facebook 提供的替代 npm 的工具，可以加速 node 模块的下载。React Native 的命令行工具用于执行创建、初始化、更新项目、运行打包服务（packager）等任务。

    npm install -g yarn react-native-cli

   安装完 yarn 之后就可以用 yarn 代替 npm 了，例如用yarn代替npm install命令，用yarn add 某第三方库名代替npm install 某第三方库名。


## Android 开发环境

**1. 安装 Android Studio**

   [国外版网址 Android Studio](https://developer.android.google.cn/studio/) 

   [国内版中文网址 Android Studio](http://www.android-studio.org/)

**2. 安装 Android SDK**
  ==你可以在 Android Studio 的欢迎界面中找到 SDK Manager。点击"Configure"，然后就能看到"SDK Manager"。==

==SDK Manager  在 Android Studio 的"Preferences"菜单中找到。 具体路径是Appearance & Behavior → System Settings → Android SDK.==

在 SDK Manager 中选择"**SDK Platforms**"选项卡，然后在右下角勾选"**Show Package Details**"。展开**Android 9 (Pie)**选项，确保勾选了下面这些组件（重申你必须使用稳定的翻墙工具，否则可能都看不到这个界面）：

	Android SDK Platform 28
	Intel x86 Atom_64 System Image（官方模拟器镜像文件，使用非官方模拟器不需要安装此组件）

然后点击"SDK Tools"选项卡，同样勾中右下角的"**Show Package Details**"。展开"**Android SDK Build-Tools**"选项，确保选中了 React Native 所必须的**28.0.3**版本。你可以同时安装多个其他版本。

最后点击"Apply"来下载和安装这些组件。

**3. 配置 ANDROID_HOME 环境变量**

==打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量 -> 新建，创建一个名为ANDROID_HOME的环境变量（系统或用户变量均可），指向你的 Android SDK 所在的目录==

SDK 默认是安装在下面的目录：

       c:\Users\你的用户名\AppData\Local\Android\Sdk
你可以在 Android Studio 的"**Preferences**"菜单中查看 SDK 的真实路径，具体是**Appearance & Behavior → System Settings → Android SDK。**

**4. 把 platform-tools 目录添加到环境变量 Path 中**

==打开控制面板 -> 系统和安全 -> 系统 -> 高级系统设置 -> 高级 -> 环境变量，选中Path变量，然后点击编辑。点击新建然后把 platform-tools 目录路径添加进去。==

此目录的默认路径为：

    c:\Users\你的用户名\AppData\Local\Android\Sdk\platform-tools

## 创建新项目

使用 React Native 命令行工具来创建一个名为"AwesomeProject"的新项目：

    react-native init  [ AwesomeProject name ]

>项目名自定义 最好是英文 大驼峰命名

**添加 react native 依赖
[ReactNavigation](https://reactnavigation.org/docs/zh-Hans/getting-started.html)

	yarn add react-navigation  or   npm install react-navigation
	yarn add react-native-reanimated react-native-gesture-handler react-native-screens@^1.0.0-alpha.23

页面路由 
    
     yarn add react-native-router-flux

[Banner 轮播 Swiper](https://github.com/leecade/react-native-swiper)

    yarn add react-native-swiper@nightly

视频

    yarn add react-native-video

# Android 测试（真机 / 模拟器）

## Android 测试 真机
[Adb工具下载安装](https://www.jianshu.com/p/7c0a6da594c8)
 [Adb devices](https://jingyan.baidu.com/article/ce4366494962083773afd3d0.html)

 连接成功 

 **vscode 打开项目** 

         安装  React Native Tools  插件


 ![安装  React Native Tools  插件](https://img-blog.csdnimg.cn/2019102322023175.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
         打开 debug 模式  **添加配置**
![打开 debug 模式  **添加配置**](https://img-blog.csdnimg.cn/20191023220321699.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
==关闭 任务管理器 java.exe 进程==
![任务管理器 java.exe 进程](https://img-blog.csdnimg.cn/20191023220638188.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
**运行应用**

    react-native run-android
![运行应用](https://img-blog.csdnimg.cn/20191023220730349.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
       
     npm run-android
![项目路径](https://img-blog.csdnimg.cn/20191023220933422.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

## Android 测试 模拟器
**使用 Android 模拟器**
你可以使用 Android Studio 打开项目下的"android"目录，然后可以使用"AVD Manager"来查看可用的虚拟设备，它的图标看起来像下面这样：

    Android Studio AVD Manager

如果你刚刚才安装 Android Studio，那么可能需要先创建一个虚拟设备。点击"**Create Virtual Device..**."，然后选择所需的设备类型并点击"Next"，然后选择Pie API Level 28 image.

译注：请不要轻易点击 Android Studio 中可能弹出的建议更新项目中某依赖项的建议，否则可能导致无法运行。

如果你还没有安装 HAXM（Intel 虚拟硬件加速驱动），则先点击"Install HAXM"或是按这篇文档说明来进行安装。

然后点击"Next"和"Finish"来完成虚拟设备的创建。现在你应该可以点击虚拟设备旁的绿色三角按钮来启动它了，启动完后我们可以尝试运行应用。

编译并运行 React Native 应用
确保你先运行了模拟器或者连接了真机，然后在你的项目目录中运行**react-native run-android：**

	cd AwesomeProject
	react-native run-android

## VSCode 配置 react 开发环境
[配置 react 开发环境](https://xiaogliu.github.io/2017/12/26/develop-react-using-vscode/)
[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)