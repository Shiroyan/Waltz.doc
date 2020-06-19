# OS

OS对象包含了系统浏览器的基本信息

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| appEnv | string | app打包环境，具体值由业务决定，通常应为develop、staging、production |
| browser | string | 浏览器环境，该容器为waltz容器时为waltz, 若不是则为others |
| containerType | string | **1.4.0新增字段，取代原来的browser字段** |
| device | string | 设备型号（只支持iOS） |
| deviceName | string | 设备名称 |
| type | string | 系统类型， iOS/android/pc |
| version | string | 系统版本 |
| supportWaltz | boolean | 该容器是否支持waltz |

```javascript
console.log(waltz.os)
```

```javascript
{
  appEnv: "staging",
  browser: "waltz",
  containerType: "waltz",
  device: "Google",
  type: "android",
  version: "9",
  supportWaltz: true
}
```

{% hint style="danger" %}
需要注意的是若Webview不支持waltz，将无法获取该对象
{% endhint %}

