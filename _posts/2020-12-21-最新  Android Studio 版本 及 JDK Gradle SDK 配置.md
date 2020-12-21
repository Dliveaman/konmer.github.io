---
layout:     post
title:      最新 Android Studio 版本 及 JDK Gradle SDK 配置
subtitle:   最新 Android Studio 版本 及 JDK Gradle SDK 配置
date:       2020-12-21
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - Android Studio
    - RN
---

# 最新 Android Studio 版本 及 JDK Gradle SDK 配置



## 1.JDK 

### 地址

https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html



### 安装

1. 默认安装到 本地 

2. 安装成功之后 会有 `jdk` 和`jre` 两个文件夹![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171555342.png)




### 配置 

`展示图`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171606751.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)




由于 JDK 安装在 系统盘，所以只有在 系统变量中新建才有用

1. 新建系统变量  `JAVA_HOME`

   ```
   变量值:   C:\Program Files\Java\jdk1.8.0_231
   ```

2. 新建系统变量 `CLASSPATH`

   ```
   变量值:   .;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
   ```

3. `Path` 变量添加值

   ```
   变量值:   %JAVA_HOME%\bin
   变量值:   %JAVA_HOME%\jre\bin
   ```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171627736.png)


### 测试

1. 管理员状态  `CMD`  输入  `java -version `

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171637289.png)


2. 管理员状态  `CMD`  输入  `javac -version `

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171643644.png)




## SDK

打开 AS   ->   Settings -> Appearance & Behavior ->  System Settings  ->  Android SDK

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171651631.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)


下载完成即可



## Gradle 版本

#### 下载地址

https://services.gradle.org/distributions/

`下载后缀为  all.zip 版本压缩包`

#### Android Studio 配置

1. 打开 AS   ->   Settings  -> Build,Execution,Deployment -> Build Tools  ->  Gradle

2. 打开 AS   ->   Settings   搜索  Gradle

配置  Gradle本地 地址

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171707490.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)


本地地址 一定加   `file:/` 

选择的是 `.zip` 压缩包 ，不是文件夹

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171713937.png)




#### 项目生成本地访问文件

AS 打开项目的  android 文件 ，AS自动生成 文件  `local.properties`

RN项目本地运行 必须要！

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171722852.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)






## RN 项目配置注意

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221171731706.png)



[个人博客](https://xw.konmer.cn/)




