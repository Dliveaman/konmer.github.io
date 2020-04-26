---
layout:     post
title:      高德地图定位(react-native-amap-geolocation)
subtitle:   高德地图定位(react-native-amap-geolocation)
date:       2020-04-26
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - React-native
---

#  高德地图定位(react-native-amap-geolocation)

 定位地址： **[react-native-amap-geolocation](https://github.com/qiuxiang/react-native-amap-geolocation)** 

## 安装

```
npm install --save react-native-amap-geolocation
```

### android

```
react-native link react-native-amap-geolocation
```

### ios

在ios目录下新建`Podfile`

```
platform :ios, '8.0'

# The target name is most likely the name of your project.
target 'Your Target' do

  # Your 'node_modules' directory is probably in the root of your project,
  # but if not, adjust the `:path` accordingly
  pod 'React', :path => '../node_modules/react-native', :subspecs => [
    'Core',
    'CxxBridge', # Include this for RN >= 0.47
    'DevSupport', # Include this to enable In-App Devmenu if RN >= 0.43
    'RCTText',
    'RCTNetwork',
    'RCTWebSocket', # Needed for debugging
    'RCTAnimation', # Needed for FlatList and animations running on native UI thread
    # Add any other subspecs you want to use in your project
  ]
  # Explicitly include Yoga if you are using RN >= 0.42.0
  pod 'yoga', :path => '../node_modules/react-native/ReactCommon/yoga'

  # Third party deps podspec link
  pod 'DoubleConversion', :podspec => '../node_modules/react-native/third-party-podspecs/DoubleConversion.podspec'
  pod 'glog', :podspec => '../node_modules/react-native/third-party-podspecs/glog.podspec'
  pod 'Folly', :podspec => '../node_modules/react-native/third-party-podspecs/Folly.podspec'

  pod 'react-native-amap-geolocation', path: '../node_modules/react-native-amap-geolocation/lib/ios'
end
```

```
pod install
```

## key

### android

https://lbs.amap.com/api/android-location-sdk/guide/create-project/get-key

![image-20200426141845690](C:\Users\xx\AppData\Roaming\Typora\typora-user-images\image-20200426141845690.png)

**[ 发布版keystore 生成方法  ]( [https://reactnative.cn/docs/signed-apk-android#%E7%94%9F%E6%88%90%E4%B8%80%E4%B8%AA%E7%AD%BE%E5%90%8D%E5%AF%86%E9%92%A5](https://reactnative.cn/docs/signed-apk-android#生成一个签名密钥) )**

**[keystore参数文档]( https://blog.csdn.net/baidu_33714947/article/details/78904750 )**

测试版 keystore 自动生成

### keystore 存放地址  



路径：项目\android\app 

![image-20200426142739657](C:\Users\xx\AppData\Roaming\Typora\typora-user-images\image-20200426142739657.png)



## 查询keystore 的SHA1值

![image-20200426143850419](C:\Users\xx\AppData\Roaming\Typora\typora-user-images\image-20200426143850419.png)

先进入当前文件夹中的  **cmd**

发布版   keystore

```
keytool -v -list -keystore my-release-key.keystore
```

**一定记住密钥库口令**

![image-20200426145239666](C:\Users\xx\AppData\Roaming\Typora\typora-user-images\image-20200426145239666.png)





测试版 keystore

```
keytool -v -list -keystore debug.keystore
```

 **密码：android** 

返回 SHA1值 例图如上



## 配置AndroidManifest.xml

### **[android  配置]( https://lbs.amap.com/api/android-location-sdk/guide/android-location/getlocation)**

### ios

  需要填写 `Bundle Identifier` 

![img](https://upload-images.jianshu.io/upload_images/4638848-d62788038fad519d.png?imageMogr2/auto-orient/strip|imageView2/2/w/830/format/webp)





## 调用 

```
import { Geolocation } from "react-native-amap-geolocation";
const geolocationInit = async () => {
  await Geolocation.init({
    ios: "key",
    android: "key"
  });

  Geolocation.setOptions({
    interval: 3000,
    distanceFilter: 20
  });

  Geolocation.addLocationListener(location => {
    console.log(location);
  });
}

geolocationInit();

Geolocation.start();   //开始定位
Geolocation.stop();   //获取到定位后需要手动关闭，持续定位ios审核不过
Geolocation.getLastLocation()；   //获取最后一次定位的位置
```

