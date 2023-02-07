## 什么是严格模式
	严格模式是 ECMAScript5 增加的概念。它是一种不同的 JavaScript 解析和执行模型，ECMAScript3 的一些不规范写法在这种模式下会被处理，对于不安全的活动将抛出错误。

## 如何启用严格模式
在整个脚本启用严格模式，只需要在脚本开头加上这一行:
```javaScript
"use strict"
```
也可以单独指定一个函数在严格模式下执行:
```javaScript
function doSomething () {
	"use strict";
	// 函数体
}
```
虽然看起来像个没有赋值给任何变量字符串，但它其实是一个 `预处理指令` 。任何支持 `JavaScript` 的引擎看到它就会切换到严格模式。

## 注意
如果使用了严格模式，就一定要确保 `"use starict"` 出现在脚本最顶部，否则严格模式可能无法启用。
```JavaScript
alert("some code");
// 下面的 "use strict" 会被忽略

"use strict";
// 严格模式没有被激活
```

没有办法取消 `"use strict"` 
没有指定可以使程序返回默认模式。一旦使用了严格模式，就没有回头路。