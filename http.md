---
description: 拦截Ajax借助原生进行转发，解决跨域问题
---

# Http

新的拦截方式直接在XMLHttpRequest层进行了拦截，不再区分`axios`和 `ajax`

同时完善了错误码的返回，以及超时时间的设置

### 开启拦截

在axios/ajax的请求头中增加字段`useNativeProxy` ，示例代码如下

```markup
axios.defaults.headers = {
  useNativeProxy: true
}
```

但会造成开发环境下请求也被代理的情况，所以要进行一些小修改

```markup
axios.defaults.headers = {
  useNativeProxy: waltz.os.supportWaltz
}
```

借助`waltz.os.supportWaltz`进行场景的区分

### 设置超时

与axios设置延迟的行为保持一致

```markup
axios.defaults.timeout = 10000
```

### 错误码

在Http原有的状态码之上，我们新增了几项错误码供H5使用

| code | description |
| :--- | :--- |
| 4000 | 发生未知错误 |
| 4001 | 网络已断开 |
| 4002 | 请求超时 |
| 4003 | SSL证书错误 |
| 4004 | DNS解析错误 |
| 4005 | SSL证书不存在 |
| 4006 | 请求参数异常 |



