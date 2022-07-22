---
id: y54sblz5mzhsw10kjugjbv3
title: Excel文件处理
desc: ''
parent: 'Stduy-node.fs文件系统'
updated: 1658482403752
created: 1658481777120
---
## 插件引入

```javaScript
yarn add node-xlsx -s
```

## 解析xlsx文件
```javaScript
const nodeXlsx = require('node-xlsx')
const sheets = nodeXlsx.parse(path)

// 获取xlsx文件的页数
console.log(sheets.length)

// 获取某一页的数据
console.log(sheets[index])

```

## 解析文件后获得数据的结构

```json
// sheets[index].data
{
  name: '' // 为 xlsx 文件的当前页的名称
  // data 是一个二维数组,每一项都是 xlsx 表中的每一行
  data: [
    [表头数据],
    [内容]
  ]
}
```