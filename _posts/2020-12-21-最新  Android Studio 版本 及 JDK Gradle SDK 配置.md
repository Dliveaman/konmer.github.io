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

2. 安装成功之后 会有 `jdk` 和`jre` 两个文件夹

   [外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-S4Vxx15V-1608539335945)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221154900466.png)]



### 配置 

`展示图`

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-AjWdSgKc-1608539335953)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221155327126.png)]

 

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

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-jlAuWRSa-1608539335956)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221155917438.png)]



### 测试

1. 管理员状态  `CMD`  输入  `java -version `

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-SmQAq0dF-1608539335960)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221160200431.png)]

2. 管理员状态  `CMD`  输入  `javac -version `

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-4Y9MItwB-1608539335962)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221160246475.png)]



## SDK

打开 AS   ->   Settings -> Appearance & Behavior ->  System Settings  ->  Android SDK

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-MHnVtQuh-1608539335965)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221162541693.png)]

下载完成即可



## Gradle 版本

#### 下载地址

https://services.gradle.org/distributions/

`下载后缀为  all.zip 版本压缩包`

#### Android Studio 配置

1. 打开 AS   ->   Settings  -> Build,Execution,Deployment -> Build Tools  ->  Gradle

2. 打开 AS   ->   Settings   搜索  Gradle

配置  Gradle本地 地址

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-XAeks5xB-1608539335967)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221161717390.png)]

本地地址 一定加   `file:/` 

选择的是 `.zip` 压缩包 ，不是文件夹

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-8zfqp0O3-1608539335968)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221161854843.png)]



#### 项目生成本地访问文件

AS 打开项目的  android 文件 ，AS自动生成 文件  `local.properties`

RN项目本地运行 必须要！

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-CC9X8Egs-1608539335970)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221162248084.png)]





## RN 项目配置注意

[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-GLu2B5Uu-1608539335971)(C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201221162813300.png)]





