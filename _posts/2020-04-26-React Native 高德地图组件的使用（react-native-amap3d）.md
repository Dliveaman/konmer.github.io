---
layout:     post
title:      React Native 高德地图组件的使用（react-native-amap3d）
subtitle:   React Native 高德地图组件的使用（react-native-amap3d）
date:       2020-04-26
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - React-native
---

# React Native 高德地图组件的使用（react-native-amap3d）

 高德地图组件 [react-native-amap3d](https://github.com/qiuxiang/react-native-amap3d) 

## 基本使用



```javascript
import {MapView} from 'react-native-amap3d'

render() {
  return <MapView style={StyleSheet.absoluteFill}/>
}
```

![img](https:////upload-images.jianshu.io/upload_images/51256-911aa143d2100b85.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 设置地图状态

所谓的地图状态包括：中心坐标（coordinate）、缩放级别（zoomLevel）、倾斜度（titl）、旋转角度（rotation）、显示区域（region）。

### 通过 coordinate、zoomLevel 设置显示区域



```javascript
<MapView
  style={StyleSheet.absoluteFill}
  coordinate={{
    latitude: 39.90980,
    longitude: 116.37296,
  }}
  zoomLevel={18}
  tilt={45}
  showsIndoorMap
/>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-bb73ccc82dfe93d5.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

### 通过 region 设置显示区域

region 由中心坐标和经纬跨度组成，相对于 zoomLevel，region 可以精确控制显示边界。



```javascript
<MapView
  style={StyleSheet.absoluteFill}
  region={{
    latitude: 39.90980,
    longitude: 116.37296,
    latitudeDelta: 0.1,
    longitudeDelta: 0.1,
  }}
/>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-9c16804220467f8c.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

### 动画过渡

通过属性控制的地图状态切换会显得比较生硬，如果希望地图状态切换是动画过渡的，可以使用 animateTo 方法。



```javascript
<MapView ref={ref => this._mapView} style={StyleSheet.absoluteFill}/>

this._mapView.animateTo({
  tilt: 45,
  rotation: 90,
  zoomLevel: 18,
  coordinate: {
    latitude: 39.97837,
    longitude: 116.31363,
  }
})
```

## 5种地图模式

目前高德地图支持5种地图模式：

- 标准（standard）
- 卫星（satellite）
- 导航（navigation）
- 公交（bus）
- 夜间（night）



```javascript
<MapView
  style={StyleSheet.absoluteFill}
  zoomLevel={14}
  mapType='satellite'
/>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-18e6268d14e0e052.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

卫星地图

![img](https:////upload-images.jianshu.io/upload_images/51256-4f9bb75d5f2b5ace.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

导航地图

![img](https:////upload-images.jianshu.io/upload_images/51256-f296d0503cc05004.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

公交地图

![img](https:////upload-images.jianshu.io/upload_images/51256-2b6ade67b76319ae.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

夜间地图

## 地图事件

目前支持的地图事件有：

-  `onPress` 点按事件
-  `onLongPress` 长按事件
-  `onLocation` 定位事件
-  `onStatusChange` 地图状态变化事件，变化过程会一直调用
-  `onStatusChangeComplete` 地图状态变化结束事件

可以通过 `event.nativeEvent` 获取事件传递过来的数据

## 定位

通过 `locationEnabled` 控制是否启用定位，通过 `locationInterval` 和 `distanceFilter` 可以控制定位频次。



```javascript
<MapView
  style={StyleSheet.absoluteFill}
  locationEnabled
  locationInterval={10000}
  distanceFilter={10}
  onLocation={({nativeEvent}) =>
    console.log(`${nativeEvent.latitude}, ${nativeEvent.longitude}`)}
/>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-1aec36cc3dafd3ca.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 添加标注点

### 默认标注点



```javascript
<MapView style={StyleSheet.absoluteFill}>
  <Marker
    active
    title='这是一个标注点'
    color='red'
    description='Hello world!'
    coordinate={{
      latitude: 39.806901,
      longitude: 116.397972,
    }}
  />
</MapView>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-1e08e7919fa1128b.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

### 可拖拽的标注点



```javascript
<Marker
  draggable
  onDragEnd={({nativeEvent}) =>
    console.log(`${nativeEvent.latitude}, ${nativeEvent.longitude}`)}
  coordinate={{
    latitude: 39.806901,
    longitude: 116.397972,
  }}
/>
```

### 自定义图片

可以通过 `image` 属性设置标注点图片，`image` 的值是图片资源的名字，对于 android 是 drawable，对于 ios 是 Images.xcassets。



```javascript
<Marker
  title='自定义图片'
  image='flag'
  coordinate={{
    latitude: 39.806901,
    longitude: 116.397972,
  }}
/>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-8d79000b5222f90e.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

### 自定义 View

除了 `image`，还可以用 View 作为标注点，更自由的控制标注点的显示。



```javascript
<Marker
  active
  title='自定义 View'
  coordinate={{
    latitude: 39.806901,
    longitude: 116.397972,
  }}
  icon={() =>
    <View style={style.marker}>
      <Text style={style.markerText}>{(new Date()).toLocaleTimeString()}</Text>
    </View>
  }
/>

const style = StyleSheet.create({
  marker: {
    backgroundColor: '#009688',
    alignItems: 'center',
    borderRadius: 5,
    padding: 5,
  },
  markerText: {
    color: '#fff',
  },
})
```

![img](https:////upload-images.jianshu.io/upload_images/51256-32a0fe133ed25f1f.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

### 自定义弹出窗口



```javascript
<Marker
  active
  coordinate={{
    latitude: 39.806901,
    longitude: 116.397972,
  }}
>
  <View style={style.infoWindow}>
    <Text>自定义弹出窗口</Text>
  </View>
</Marker>

const style = StyleSheet.create({
  infoWindow: {
    backgroundColor: '#8bc34a',
    padding: 10,
    borderRadius: 10,
    elevation: 4,
    borderWidth: 2,
    borderColor: '#689F38',
  },
})
```

![img](https:////upload-images.jianshu.io/upload_images/51256-3a044011e013c1a0.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 绘制线段



```javascript
<MapView zoomLevel={10} style={StyleSheet.absoluteFill}>
  <Polyline
    width={10}
    color='rgba(255, 0, 0, 0.5)'
    coordinates={[
      {
        latitude: 40.006901,
        longitude: 116.097972,
      },
      {
        latitude: 40.006901,
        longitude: 116.597972,
      },
      {
        latitude: 39.706901,
        longitude: 116.597972,
      },
    ]}
  />
</MapView>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-119b602a70ea4021.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 热力图



```javascript
import {MapView, HeatMap} from 'react-native-amap3d'

_coordinates = (new Array(200)).fill(0).map(i => ({
  latitude: 39.5 + Math.random(),
  longitude: 116 + Math.random(),
}))

<MapView zoomLevel={9} style={StyleSheet.absoluteFill}>
  <HeatMap
    opacity={0.8}
    radius={20}
    coordinates={this._coordinates}/>
</MapView>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-8f7a74a29bb53251.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 海量点

批量添加的 Marker 数量过多会出现性能问题，这时可以考虑用海量点（MultiPoint）。



```javascript
import {MapView, MultiPoint} from 'react-native-amap3d'

_points = Array(1000).fill(0).map(i => ({
  latitude: 39.5 + Math.random(),
  longitude: 116 + Math.random(),
}))

_onItemPress = point => Alert.alert(this._points.indexOf(point).toString())

<MapView zoomLevel={10} style={StyleSheet.absoluteFill}>
  <MultiPoint
    image='point'
    points={this._points}
    onItemPress={this._onItemPress}
  />
</MapView>
```

![img](https:////upload-images.jianshu.io/upload_images/51256-bd06e2910c7a36e5.png?imageMogr2/auto-orient/strip|imageView2/2/w/300/format/webp)

## 更多示例

请参考 [examples](https://github.com/qiuxiang/react-native-amap3d/tree/master/example)。

