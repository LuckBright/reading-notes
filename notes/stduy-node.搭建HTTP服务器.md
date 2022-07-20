---
id: cwvahm91m3mlyo34nizrte2
title: 搭建HTTP服务器
desc: ''
parent: 'Stduy-node'
updated: 1658302376579
created: 1658301875214
---
## 搭建一个简单的 HTTP 服务器

### 示例
```
const http = require('http')

const port = 3000

const server = http.createServer((req, res) => {
  res.statusCode = 200 
  res.setHeader('Content-Type', 'text/plain')
  res.end('你好世界\n')
})
// hostname 默认为启动本地 localhost:
server.listen(port, () => {
  console.log(`服务器运行在 http://${hostname}:${port}/`)
})
```
