---
layout:     post
title:      Github下载React-native 项目运行SDK报错
subtitle:   Github下载React-native 项目运行SDK报错
date:       2019-11-03
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - Github React-native
---

# Github下载React-native 项目运行SDK报错

## * What went wrong: A problem occurred configuring project ':app'. > SDK location not found. Define location with an ANDROID_SDK_ROOT environment variable or by setting the sdk.dir path in your project's local properties file at 'F:\Example\demos\android\local.properties'.

原因：git下来的项目找不到本地SDK

解决方案：配置本地SDK路径

## 1.Android-studio 查询本地SDK路径
[Android Studio设置或修改Android SDK路径](https://jingyan.baidu.com/album/c1465413e068770bfcfc4cfb.html?picindex=1)

打开Android studio，点击“File”菜单下的“Other Settings”，接着点击“Default Project Structure”选项。

![在这里插入图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdzYS5iYWlkdS5jb20vZXhwL3c9NDgwL3NpZ249YWFlYzg0NzcxNWQ4YmMzZWM2MDgwN2MyYjI4YWE2YzgvZDMxYjBlZjQxYmQ1YWQ2ZTFiYTk1NWE3OGRjYjM5ZGJiNmZkM2MyZS5qcGc?x-oss-process=image/format,png)
这时就会看到SDK Location，点击图示第二个红色区域的图标，就可以修改默认的AndroidSDK路径。
![在这里插入图片描述](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWdzYS5iYWlkdS5jb20vZXhwL3c9NDgwL3NpZ249MmEwMWZlN2U5ZTQ1ZDY4OGEzMDJiM2FjOTRjMzdkYWIvYWE2NDAzNGY3OGYwZjczNjQ2M2Y3YjRjMDY1NWIzMTllYWM0MTNiZC5qcGc?x-oss-process=image/format,png)

## 复制本地SDK地址，存放Git项目中
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191103094858872.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191103095132753.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70)

重新 在项目 cmd中执行 react-native run-android