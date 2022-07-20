---
id: 69qm1st1mevo3j3m83aej5k
title: 执行GET、POST请求
desc: ''
parent: 'Stduy-node.搭建HTTP服务器'
updated: 1658309247040
created: 1658303113881
---
## 初始化服务
使用 `http.createServer()` 创建 Server 服务
```
  var server = http.createServer()
  server.on('request', callback(request, response))
```

## 监听事件 `request`，每次有请求时都会触发此事件
- callback 回调事件提供两个参数
>- * request 请求对象。用于访问响应状态、消息头、以及数据
>- * response 访问对象。由 HTTP 服务器在内部创建， 它作为第二个参数传给 `request` 事件

- 示例
```
const server = http.createServer()
server.on('request', (req, res) => {
  const url = req.url
  if (url === '/') {
    fs.readFile(__dirname + '/index.html', (err, data) => {
      if (!err) {
        // 设置请求头
        res.writeHead(200, { "Content-Type": "text/html;charset=UTF-8" })
        res.end(data)
      } else {
        throw err
      }
    })
  }
  if (url === '/data') {
    fs.readFile(__dirname + '/path/file.txt', (err, data) => {
      if (!err) {
        // 设置请求头
        res.writeHead(200, { "Content-Type": "text/html;charset=UTF-8" })
        res.end(data.toString())
      } else {
        throw err
      }
    })
  }
  if (url === '/getData') {
    console.log('触发到这里了')
    res.writeHead(200, { "Content-Type": "text/html;charset=UTF-8" })
    res.end(JSON.stringify({
      'msg': 'Hello World!我是createServer'
    }))
  }
})
```
## 启动 HTTP 服务器监听连接
```
server.listen('端口号', () => {...})
```