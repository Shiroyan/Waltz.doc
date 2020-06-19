# Changelog

## 1.4.1

### Feature

* PC端`service`模块新增sendMessage方法，以便与第三方应用通讯

## 1.4.0

### Feature

* `service`模块新增[`launchApp`](bridge.md#launchapp), [`launchAppForResult`](bridge.md#launchappforresult-only-mobile), [`launchOnlineApp`](bridge.md#launchonlineapp-only-mobile) 方法
* [`os`](os.md)新增`deviceName`以区分`device`字段

## 1.3.0

### Feature

* PC端，新增事件`message`用于处理来自其它应用的数据

## 1.2.2

### Fix

* 修复Hook在处理参数时，转义错误的问题

## 1.2.1

### Breaking Change

对原有的Http拦截方式进行废弃，引入更友好更健壮的方式， 详见[Http](http.md) **（contributed by wenyf001）**

## 1.1.6

### Added

* `window.open`方法新增`animated`参数，控制是否开启过渡动画

## 1.1.5

### Added

* `setStatusBar`现已支持iOS，[详情](bridge.md###setStatusBar)

## 1.1.5-alpha.3

### Added

* 暴露`waltz`在`Window`下

### **Changed**

* [原生返回的数据](jie-shao.md)中，body支持string

### **Fixed**

* 修复内置事件返回的数据体为指针的问题
* 修复`window.open`方法会多次调用的问题

## 1.1.5-alpha.2

### Added

* 支持使用`Vue.use`进行使用
* [AxiosHook](http.md#axioshook) &  [AjaxHook](http.md#ajaxhook)增加新的调用方式

### **Changed**

* 在执行回调时，若报错仍然把错误抛出给开发者处理

### **Fixed**

* 修复启用Http后，获取参数时出错的问题

## 1.1.5-alpha.1

### Added

#### System

* 新增[showKeyboard](bridge.md#showkeyboard), [hideKeyboard](bridge.md#hidekeyboard)方法

#### File

* 新增[select](bridge.md#select), [upload](bridge.md#upload)方法

### **Fixed**

* 修复原生调用JS时，因`decodeURIComponent`报错的问题
* 修复OS获取device时，取值错误的问题

## 1.1.4

### Added

* `Event` 暴露 `once`方法

### **Fixed**

* 修复`supportWaltz`变量无法访问的问题

## 1.1.3

### Added

#### File

* 新增[onlinePreview](bridge.md#onlinepreview)方法查看文件

### Changed

* 优化native部分代码，提取公共方法作为Base类

## 1.1.2

### Added

#### OS

* 新增`supportWaltz`判断当前环境是否支持waltz

#### File

* 新增模块，支持[download](bridge.md#download)、[open](bridge.md#open)功能

### Fixed

* 修复`Waltz`在Android 5报错的情况
* 修复`Waltz`环境探测能力，用户直接调用请求接口，无需关注是在`Waltz`环境下还是其他环境中

## 1.1.1

### Changed

统一处理原生返回的数据

* 原来android和iOS返回的数据格式不一，导致需要在业务中进行转换；在开发中发现这种操作非常的费时费力，故统一在sdk中进行处理

  ```javascript
  // before
  waltz.call({
    module: 'coco',
    handlerName: 'getUserInfo'
  })
    .then(res => {
      let data = waltz.os.type === 'android' 
        ? JSON.parse(res.data.body)
        : res.data.body
    })
    .catch(err => {})

  //  now 
   waltz.call({
    module: 'coco',
    handlerName: 'getUserInfo'
  })
    .then(res => {
      let data = res.data.body
    })
    .catch(err => {})
  ```

