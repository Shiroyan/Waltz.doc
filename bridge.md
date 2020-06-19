---
description: bridge是js与native的桥梁，用于两者的通讯
---

# Bridge

waltz对各种原生能力进行友好的模块划分，分别为

* navigator
* window
* components
* system
* service
* call
* register

## navigator

### setTitle

设置导航栏标题

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| title | string | 是 | 导航栏的标题头 |
| color | string | 是 | 导航栏字体的颜色，十六进制色值，如：\#dd2efa |
| size | number | 是 | 字体大小 |

```javascript
waltz.navigator.setTitle({
  title: '窗口体系首页',
  color: '#e72229',
  size: 30
})
```

### setBackgroundColor

设置导航栏背景色

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| color | string | 是 | 背景的颜色，十六进制色值，如：\#dd2efa |

```javascript
waltz.navigator.setBackgroundColor('#00ffff')
```

### setStatusBar

设置手机状态栏

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| black | boolean | 否 | 对于Android，设置状态栏字体颜色，只支持黑白二色，true为黑色， false为白色； 对于iOS，true为dark主题，false为light主题 默认为false |
| backgroundColor | string | 是 | 状态栏背景色 十六进制色值，不支持\#fff这种缩写； **注意该参数仅在Android有效** |

```javascript
waltz.navigator.setStatusBar({
  black: true,
  background: '#ffffff'
})
```

### show

展示导航头

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |


无

```javascript
waltz.navigator.show()
```

### hide

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |


无

```javascript
waltz.navigator.hide()
```

## window

### back

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| index | number | 否 | 往前返回几页，1表示前一个页面，2表示前两个页面；数字大于导航栏栈中的数量时不做任何处理；传入不符合要求的数字时（如负数，小数，字符等）不做任何处理 |

```javascript
waltz.window.back(1)
```

### close

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |


无

```javascript
waltz.window.close()
```

### open

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| url | string | 是 | 跳转新的轻应用链接 |
| animated | boolean | 否 | 是否开启跳转动画, 默认为true |
| tipsTitile | string | 否 | 打开轻应用时的提示标题头 |
| tipsMessage | string | 否 | 打开轻应用时的提示消息体 |

```javascript
waltz.window.open({
  url: 'https://www.baidu.com',
  animated: true,
  tipsTitile: '正在切换轻应用',
  tipsMessage: '正在打开百度'
})
```

### jump

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| url | string | 是 | 同一个轻应用中跳转不同页面的链接，绝对路径 |

```javascript
const arr = window.location.href.split('/')
waltz.window.jump(window.location.href.split(arr[arr.length - 1])[0] + 'test3.html')
```

### setBounces

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| bounces | Boolean | 否 | 是否开启iOS回弹效果 |

```javascript
waltz.window.setBounces(true)
```

## file

### download

下载文件

**入参**

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| method | string | 是 | 下载文件的方法，get/post |
| url | string | 是 | 下载文件的url，绝对路径 |
| headers | object | 否 | 请求头参数，如果该下载接口需要一些额外的参数一并写入该参数内 |
| data | object | 否 | 当method为post时，请求参数放在此处 |

**返回**

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| filePath | string | 是 | 文件存放的路径 |

```javascript
waltz.file.download({
  url: 'http://xxxxx/files',
  header: {
    Authorization: 'token'
  }
})
  .then(({data}) => {
    console.log(data.filePath)
  })
```

### open

打开文件

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| path | string | 是 | 下载文件的url，绝对路径 |

```javascript
waltz.file.open({
  path: data.filePath
})
```

### upload

上传文件

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| url | string | 是 | 接口地址，绝对路径 |
| header | object | 是 | 请求头部信息 |
| data | object | 否 | 表单额外字段 |
| files | Array | 是 | 需要上传的文件路径 |

```javascript
waltz.file.upload({
  url: 'http://10.200.93.44/files',
  header: {
    Authorization: 'Bearer xxxxxx'
  },
  data: {
    id: '1234' 
  },
  files: [
    '/sys/files/abc.png'
  ]
})
```

### onlinePreview

在线预览文件

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| urls | String\[\] | 是 | 文件路径数组 |

```javascript
waltz.file.onlinePreview([
    'urls/imge1.png',
    'urls/image2.png'
])
```

## system

### showKeyboard

参数：无

```javascript
waltz.system.showKeyboard()
```

### hideKeyboard

参数：无

```javascript
waltz.system.hideKeyboard()
```

## service

此模块包含大多数业务场景api， 返回内容具体与业务开发人员协商

### getToken（only mobile）

获取登录token

```javascript
waltz.service.getToken()
  .then(data => {

  })
  .catch(e => {

  })
```

### getUserInfo（only mobile）

获取登录人员信息

```javascript
waltz.service.getUserInfo()
  .then(data => {

  })
  .catch(e => {

  })
```

### launchApp

打开第三方轻应用

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| appid | string | 是 | 轻应用id |
| serviceId | string | 否 | 服务id，在轻应用平台进行配置 |
| data | any | 否 | 传递给应用的参数，需与相关业务方协商 |

```javascript
waltz.service.launchApp(appid, serviceId, data)
```

### launchAppForResult（only mobile\)

打开轻应用并等待返回结果

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| appid | string | 是 | 轻应用id |
| data | any | 否 | 传递给应用的参数，需与相关业务方协商 |
| link | string | 否 | 如果需要打开指定地址，请设置此参数，注意该参数是绝对地址 |

返回

`Promise`

```javascript
waltz.service.launchAppForResult(appid, data, link)
    .then(data => {})
    .catch(err => {})
```

### launchOnlineApp \(only mobile\)

打开指定地址的轻应用

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| appid | string | 是 | 轻应用id |
| data | any | 否 | 传递给应用的参数，需与相关业务方协商 |
| link | string | 否 | 如果需要打开指定地址，请设置此参数，注意该参数是绝对地址 |

返回

`Promise`

```javascript
waltz.service.launchOnlineApp(appid, data, link)
    .then(data => {})
    .catch(err => {})
```

### sendMessage\(only PC\)

向别的轻应用发送消息/传送数据

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| data | any | 是 | 传递给应用的参数，需与相关业务方协商 |
| type | string | 否 | Tab级别的应用名称，可选值有schedule，task\_center，app\_center |
| appid | string | 否 | 应用id |
| autofocus | string | 否 | 是否需要自动聚焦到对应应用的Tab上，只支持Tab级应用 |

{% hint style="warning" %}
`type`和`appid`必传其中之一
{% endhint %}

无返回

```javascript
waltz.sevice.sendMessage(data, type, appid, autofocus)
```

## call

waltz可能并没有考虑得那么周到，亦或者有些原生能力属于业务范畴； 这个时候就可以使用这个方法，自行去调用原生能力

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| module | String | 是 | 模块名，这个需要与原生开发人员协商 |
| handlerName | String | 是 | 方法名，也是与原生开发协商 |
| data | Any | 否 | 传递给原生的参数 |

返回

`Promise`

```javascript
waltz.call({
  module: 'WZToken',
  handlerName: 'getToken',
  data: {}
})
  .then(data => {})
  .catch(err => {})
```

## register

当原生需要调用js方法时，使用此方法注册方法提供给原生调用。

```javascript
waltz.register('refresh', () => {
  window.location.reload()
})
```

{% hint style="warning" %}
需要注意的是，反复注册时，会直接覆盖原有的方法
{% endhint %}

| 参数 | 类型 | 必填 | 说明 |
| :--- | :--- | :--- | :--- |
| handlerName | String | 是 | 方法名，与原生开发协商 |
| callback | Function | 是 | 供原生调用的方法 |

{% hint style="danger" %}
`window-focus window-blur window-destroy`这三个方法名已被框架占用
{% endhint %}

