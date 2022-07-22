---
id: em7qq5i4ewbaecxhtxqa01z
title: Fs文件系统
desc: ''
parent: 'Stduy-node'
updated: 1658482893791
created: 1658299640698
---
## 什么是 fs 文件系统模块
fs 模块是 Node.js 官方提供的，用来操作文件的模块。它提供了一系列的方法和属性，用来满足用户对文件的操作需求

- `fs.readFile()` 方法，用来读取指定文件中的内容
- `fs.writeFile()` 方法，用来向指定文件中写内容

## 如何使用？
使用 `require` 函数导入 fs 模式

```
  const fs = require('fs')
```

### 注意
大部分方法都有两种模式：`同步` 和 `异步`
- 示例
```
fs.writeFile() // 异步
fs.writeFileSync() // 同步
```

## 语法篇

### `fs.readFile()` 读取文件
- `fs.readFile()` 语法格式
```
  fs.readFile(path[, options], callback)

  参数1 path       : 必选参数，字符串，表示文件的路径
  参数2 [, options]: 可选参数，表示以什么编码格式来读取文件，一般默认指定 utf8
  参数3 callback   : 必选参数，文件读取完成后，通过回调函数拿到读取结果
```

- 示例
  获取 path 文件夹中 file.txt 文件内容
  ```
  fs.readFile(__dirname + '/path/file.txt', (err, data) => {
      if (!err) {
        console.log(data) // 取到的是一个 Buffer
        console.log(data.toString()) // 取到内容 我第一次写入这个文件我第二次写入这个文件
      } else {
        throw err // 没有取到，抛出错误
      }
    })
  ```

### `fs.writeFile()` 写入文件
- `fs.writeFile()` 语法格式
```
  fs.writeFile(file,data[, options], callback)

  参数1 file       : 必选参数，指定一个文件路径的字符串，表示文件的存放路径
  参数2 data       : 必选参数，表示要写的内容
  参数3 [, options]: 可选参数，表示以什么编码格式来写入文件，默认值 utf8
  参数4 callback   : 必选参数，文件写入完成后的回调函数
```

- 示例
向指定的文件路径中，写入文件内容
```javaScript
const content = '我第二次写入这个文件'

fs.writeFile(__dirname + '/path/file.txt', content, err => {
  if (err) {
    console.error(err)
    return
  }
  //文件写入成功。
})
```

