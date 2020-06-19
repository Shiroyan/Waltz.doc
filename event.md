# Event

目前只实现了几类事件，eventName\(事件名\)分别为

* native-call-js
* native-call-js-success
* native-call-js-error
* js-call-native
* js-call-native-success
* js-call-native-error
* window-focus
* window-blur
* window-destroy
* message

## 例子

每一类事件返回的内容都不一样

```javascript
waltz.event.on('native-call-js', msg => {

})
```

## 各事件返回的内容

* **native-call-js** 和 **native-call-js-success**

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| msg | String，Object | 返回信息 |

* **native-call-js-error**

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| code | String | 错误码，目前阶段暂时未定案 |
| msg | String | 错误消息 |
| err | Object | js的Error对象 |

* **js-call-native** 和 **js-call-native-success**

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| module | String | 模块名 |
| handlerName | String | 句柄名 |
| handlerMethod | Number | 区分以何种方式调用原生 |
| data | Object | 调用原生时传递的数据内容 |

* **js-call-native-error**

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| msg | String | 错误消息 |

* **window-\***

window类事件无返回内容

* **message**

返回的参数与业务方协商

