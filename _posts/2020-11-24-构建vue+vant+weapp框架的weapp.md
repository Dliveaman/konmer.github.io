---
layout:     post
title:      vue vant weapp 搭建小程序项目，以及打包发布( vue 小程序项目 )
subtitle:   vue vant weapp 搭建小程序项目，以及打包发布( vue 小程序项目 )
date:       2020-11-24
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - Weapp小程序
    - Vue
---
## vue+vant+weapp搭建小程序，以及打包发布

##  vue环境搭建

1. 安装node：进入[node官网下载](https://nodejs.org/zh-cn/download/)与系统匹配的安装包完成安装

2. 安装vue：查看[官网教程](https://cn.vuejs.org/v2/guide/installation.html)完成安装

   

## 构建 weapp

1. 打开 `微信开发者工具 ` 新建项目

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201124095112533.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)


2.打开  新建项目  根目录 下的 cmd命令编辑器
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201124095140547.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)

3.初始化项目 

```
(输入命令之后一直点回车)
npm init 
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201124095222691.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)

4.安装 vant-weapp UI框架

```
 npm i vant-weapp
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201124095235698.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)

5.设置 新建项目   `使用npm模块`

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020112409530023.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)

6.在 `微信开发者工具 ` 中   
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201124095308738.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)
7.构建 vue + vant + weapp 小程序项目 完成

![在这里插入图片描述](https://img-blog.csdnimg.cn/2020112409533323.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDY2NjExNg==,size_16,color_FFFFFF,t_70#pic_center)

## 打包发布

当小程序开发完毕后，我们需要把程序发布上去。

1. 点击上传按钮，按提示操作，填入版本及描述，完成上次
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200312131557356.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU0MDk3Nw==,size_16,color_FFFFFF,t_70)
   ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200312131721587.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU0MDk3Nw==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200312131824923.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU0MDk3Nw==,size_16,color_FFFFFF,t_70)
2. 登录小程序账号，查看版本管理，可以看到我们提交的版本。![在这里插入图片描述](https://img-blog.csdnimg.cn/20200312132146942.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU0MDk3Nw==,size_16,color_FFFFFF,t_70)



参考文档

1.https://blog.csdn.net/weixin_46540977/article/details/104812315