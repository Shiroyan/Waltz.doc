# 快速入门

## npm （推荐）

```javascript
npm i git+http://git.dev.cmrh.com/FrontEnd/WaltzSDK/JS.git
```

在`main.js`中

```javascript
import waltz from 'waltz.js'
```

如果你的项目是一个Vue项目

```javascript
Vue.use(waltz)
```

然后在`.vue`文件中, 通过以下方式进行调用

```javascript
this.$waltz.navigator.show()
```

## script

下载

点击[这里](http://git.dev.cmrh.com/FrontEnd/WaltzSDK/JS/blob/master/dist/waltz.min.js)获取最新的文件

```markup
<script src="waltz.min.js"></script>
<script>
  window.waltz.navigator.setTitle({
    title: '主页',
    color: '#333',
    size: 17
  })
</script>
```

