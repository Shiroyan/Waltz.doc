# 介绍

## Demo

```javascript
waltz.navigator.show()
  .then(data => {})
  .catch(err => {})
```

所有调用原生的方法，均会返回一个`Promise`， 原生返回的数据可以在`.then`中获取

## 原生返回的数据

```javascript
{
  id: "26e52944-6818-4141-9afd-e641070619fb", //..回调的id
  data: {
    msg: "hideNavigationBar callback", 
    body: {}, //..object, JSONString, string
    code: "10000" //..状态码
  }
}
```

## 错误返回

```javascript
{
  id: "26e52944-6818-4141-9afd-e641070619fb", //..回调的id
  data: {
    msg: "hideNavigationBar callback error", 
    body: {}, //..额外参数
    code: "10001" //..状态码
  }
}
```

接下来为大家介绍Waltz里面的Api

