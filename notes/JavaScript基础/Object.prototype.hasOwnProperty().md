	  hasOwnProperty() 方法返回一个布尔值,查看对象自身属性中是否包含指定的属性。

```javaScript
const obj1 = {}
obj.a = 42;

obj1.hasOwnProperty('a');
// 返回 true
obj1.hasOwnProperty('b');
// 返回 false
obj1.hasOwnProperty('hasOwnProperty');
// 返回 false
```