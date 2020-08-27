---
layout:     post
title:      React Native 内嵌webview ( Vue项目 )
subtitle:   React Native 内嵌webview ( Vue项目 )
date:       2020-08-03
author:     Konmer
header-img: img/post-web.jpg
catalog: true
tags:
    - React-native
    - Vue
---



# React Native 内嵌webview ( Vue项目 ) 

## ReactNative webview

### 属性

- automaticallyAdjustContentInsets
   控制是否调整放置在导航条、标签栏或工具栏后面的web视图的内容。默认值为true
- contentInset {top: number, left: number, bottom: number, right: number}
   设置网页内嵌边距
- injectedJavaScript
   设置在网页加载之前注入一段js代码
- mediaPlaybackRequiresUserAction
   设置页面中的HTML5音视频是否需要在用户点击后再开始播放。默认值为true
- scalesPageToFit
   设置是否要把网页缩放到适应视图的大小，以及是否允许用户改变缩放比例。
- source
   在WebView中指定加载内容html或者url,可以指定header,method等
- startInLoadingState
   强制WebView在第一次加载时先显示loading视图。默认为true
- domStorageEnabled（android）
   布尔值,指定是否开启DOM本地存储
- javaScriptEnabled（android）
   布尔值,指定WebView中是否启用JavaScript。只在Android上使用，因为在iOS上默认启用了JavaScript。
- mixedContentMode(android)
   指定混合内容模式。即WebView是否应该允许安全链接（https）页面中加载非安全链接（http）的内容,
  - 'never' (默认) - WebView不允许安全链接页面中加载非安全链接的内容
  - 'always' - WebView允许安全链接页面中加载非安全链接的内容。
  - 'compatibility' - WebView会尽量和浏览器当前对待此情况的行为一致
- userAgent(android)
   为WebView设置user-agent字符串标识。这一字符串也可以在原生端用WebViewConfig来设置，但js端的设置会覆盖原生端的设置。
- allowsInlineMediaPlayback（ios）
   指定HTML5视频是在网页当前位置播放还是使用原生的全屏播放器播放。 默认值为false,视频在网页播放还需要设置webkit-playsinline
- bounces(ios)
   指定滑动到边缘后是否有回弹效果。
- decelerationRate（ios）
   指定一个浮点数，用于设置在用户停止触摸之后，此视图应以多快的速度停止滚动。也可以指定预设的字符串值，如"normal"和"fast"，
- scrollEnabled（ios）
   是否启用滚动

### 函数

- injectJavaScript
   函数接受一个字符串，该字符串将传递给WebView，并立即执行为JavaScript
- onError
   加载失败时回调
- onLoad
   完成加载时回调
- onLoadEnd
   加载成功或者失败都会回调
- onLoadStart
   开始加载的时候回调
- onMessage
   在webView内部网页中，调用window.postMessage可以触发此属性对应的函数，通过event.nativeEvent.data获取接收到的数据，实现网页和RN之间的数据传递
- renderError
   返回一个视图用来提示用户错误
- renderLoading
   返回一个加载指示器
- onShouldStartLoadWithRequest(ios)
   请求自定义处理，返回true或false表示是否要继续执行响应的请求

## 实操

### 1. react-native-webview

```
npm i react-native-webview
```

#### ReactNative 页面引用

```
import { WebView } from 'react-native-webview';
```

### 2.webview 代码

```
WebView ref={ (webView) => this.webView = webView }
                    originWhitelist={ ['*'] }
                    javaScriptEnabled={ true }
                    // 开启缓存
                    // domStorageEnabled={ true }
                    thirdPartyCookiesEnabled={ true }
                    // 允许文件上传
                    allowFileAccess={ true }
                    onMessage={ this._onMessage }
                    onLoad={() => { this.handleInjectJavascript();
                    }} //初始化调用方法
                    useWebKit={true}
                    // 加载时强制使用loading转圈视图，注意如果为true，在低性能下，webview可能会加载失败，显示为空白
                    startInLoadingState={false}
                    // webview加载错误页面
                    renderError={this.renderErrorView} // 页面无网络报错调用方法
                    source={ {uri: 'http://www.baidu.com/'} } // 网络路径
                    // source={ {uri: 'http://192.168.1.1111:8080/'} }  //本地路径
                />
```

### 3.RN -> Vue 

#### RN 页面

**onLoad 函数**

在webview初始化source前执行的函数，通常是调用一个方法

```
onLoad={() => { this.handleInjectJavascript('hello,vue'); }}
```

**handleInjectJavascript()**方法才是真正用于给 Vue 或者 Html 页面发送数据

```
 //RN webview 向 vue发送数据
 handleInjectJavascript = (data) => {
     const injectJavascriptStr =  `(function() {
     	window.WebViewBridge.onMessage(${JSON.stringify(data)});
     })()`; // 拼接 数据 为 方法
     if(this.webView) {
     	this.webView.injectJavaScript(injectJavascriptStr)
     } //   通过 injectJavaScript  将 数据 传递给WebView页面，并立即执行为js
 }
```

#### Vue 页面

```
 mounted() {
 	window.WebViewBridge = {
      onMessage: this._onMessage //在window上挂载一个onMessage方法，RN会调用
    }
    const event = new Event('WebViewBridge')
    window.dispatchEvent(event);
 },
 methods: {
    // 接收rn发送消息
    _onMessage(data) {
      let that = this;
      console.log('data -------  ',JSON.stringify(data)); //  'hello,vue'
    }
  }
```

**注意: react native 页面 初始化 字面量的 拼接方法名 onMessage 必须跟 vue页面的 mounted() 中 onMessage:this._onMessage 一致**

**解释：rn中 给 window.WebViewBridge 增加一个名为 onMessage 的方法，vue初始化页面会对应给出onMessage 指向的方法，在此代码块 指向 _onMessage 方法**



### 4.Vue -> RN 

#### Vue 页面

```
  mounted() {
   	const event = new Event('WebViewBridge')
    window.dispatchEvent(event);
  },
  methods: {
    // 向rn发送消息
    _postMessage('wow,RN!!') {
        window.ReactNativeWebView.postMessage(data);
        // 将值 'wow,RN!!' 挂载到 postMessage 
    }
  }
```

#### RN 页面

**onMessage  函数** 

在接收到 vue 传输的数据之后 执行的方法

```
onMessage={ this._onMessage }
```

**_onMessage**方法获取 Vue 或者 Html 页面返回的 数据

```
 // 接受vue发送来的消息
 _onMessage = (event) => {
        console.log('接收vue发来的消息onMessage', event.nativeEvent.data); 
        // '接收vue发来的消息onMessage wow,RN!!'
  }
```



### 5. RN < -- > Vue   (多次双向传值) 

基于 vue -> rn **拓展**

#### Vue 页面

```
  mounted() {
  	window.WebViewBridge = {
      onMessage: this._onMessage,
      receiveMessage: this._receiveMessage //在window上挂载一个receiveMessage方法，RN自行调用
    }
  	
   	const event = new Event('WebViewBridge')
    window.dispatchEvent(event);
  },
  methods: {
    // 向rn发送消息
    _postMessage('wow,RN!!') {
        window.ReactNativeWebView.postMessage(data);
        // 将值 'wow,RN!!' 挂载到 postMessage 
    },
    // 二次或多次接收rn发送消息
     _receiveMessage(data){
      let that = this;
      console.log('data receiveMessage-------  ',JSON.stringify(data));
     }
  }
```

#### RN 页面

**onMessage  函数** 

在接收到 vue 传输的数据之后 执行的方法

```
onMessage={ this._onMessage }
```

**_onMessage**方法获取 Vue 或者 Html 页面返回的 数据

```
 // 接受vue发送来的消息
 _onMessage = (event) => {
        console.log('接收vue发来的消息onMessage', event.nativeEvent.data); 
        // '接收vue发来的消息onMessage wow,RN!!'
        
        const injectJavascriptStr =  `(function() {
 			window.WebViewBridge.receiveMessage(${JSON.stringify('hello,vue2!!! ')});
        })()`;
        this.webView.injectJavaScript(injectJavascriptStr);
  }
```



**参考文档：**

1.[ReactNative WebView组件详解](https://www.jianshu.com/p/9e6f1569227f)

2.[WebView组件介绍](https://www.hangge.com/blog/cache/detail_1564.html)

3.[问题解决库](https://github.com/react-native-community/react-native-webview/issues)