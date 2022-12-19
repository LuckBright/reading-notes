---
id: jatgs1zlipq7g7cglg5e0rz
title: 模块
desc: 'ES2015 在 javascript 标准中引入了一种官方的模块功能'
updated: 1671429988897
created: 1671071007711
---

### 一个模块导出多个方法

```javascript
const circleArea = r => 3.14 * (r ** 2)
const squareArea = s => s * s
export { circleArea, squareArea }

// 在导出的时候就对函数进行重命名
export { circleArea as circle, squareArea as square }
```

以上表示代码表示我们暴露了两个函数，以便其它文件使用。只有被导出的成员才对其他模块或文件可见。

### 如何导入其他模块提供的函数

```javascript
import { circleArea, squareArea } from './area'
```

以上是从一个模块导入多个函数，也可只导入一个。

### 导入函数后对其重命名

```javascript
import { circleArea as circle } from './area'
```

### 将模块整个导入，像使用类一样使用这个模块下面的函数

```javascript
import * as area from './area'

// 使用
area.circleArea(2)
area.squareArea(2)
```

### 如果模块只有一个成员，可以使用 export default 将其整个导出

```javascript
export default class Book {
  constructor (title) {
    this.title = title
  }
  printTitle () {
		console.log(this.title)
  }
}
```

###  使用上面整个被导出的模块

```javascript
import Book from './17-Book'
const myBook = new Book('some title')
myBook.printTitle()
```

