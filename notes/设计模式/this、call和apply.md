### this
	javaScript 的 this 总是指向一个对象，具体指向哪个对象是在运行时基于函数的执行环境动态绑定，而非函数被声明时的环境。

在实际应用中，this 的指向大致分为以下4中：
- [作为对象的方法调用。](#作为对象的方法调用)
- [作为普通函数调用。](#作为普通函数调用。)
- [构造器调用。](#构造器调用。)
- [Functions.prototype.call 或者 Function.prototype.apply 调用。](#Functions.prototype.call 或者 Function.prototype.apply 调用。)

### 作为对象的方法调用
this 指向被调用的对象
```javaScript
var obj = {
    a: 1,
    getA: function(){
        alert ( this === obj );    // 输出：true
        alert ( this.a );    // 输出: 1
    }
};

obj.getA();
```

### 作为普通函数调用。
当函数不做为对象的属性被调用，this 指向全局对象。在浏览器的 JavaScript 中，全局对象指的是 Window 对象
```JavaScript
window.name = 'globalName';

var getName = function(){
    return this.name;
};

console.log( getName() );    // 输出：globalName

// 或者

window.name = 'globalName';

var myObject = {
    name: 'sven',
    getName: function(){
        return this.name;
    }
};

var getName = myObject.getName;
console.log( getName() );    // globalName

```

### 构造器调用。
当用 new 运算符调用构造器函数的时候，this 指向 **函数返回的这个对象。** 
```JavaScript
var MyClass = function(){
    this.name = 'sven';
    return {    // 显式地返回一个对象
        name: 'anne'
    }
};

var obj = new MyClass();
alert ( obj.name );     // 输出：anne
```

当构造器函数不显示的返回任何数据，或者返回一个非对象类型的数据，则指向构造函数内部的数据。
```JavaScript
var MyClass = function(){
    this.name = 'sven'
    return 'anne';    // 返回string类型
};

var obj = new MyClass();
alert ( obj.name );     // 输出：sven
```
### Functions.prototype.call 或者 Function.prototype.apply 调用。
可以动态地改变传入函数的 this：
```JavaScript
var obj1 = {
    name: 'sven',
    getName: function(){
        return this.name;
    }
};

var obj2 = {
    name: 'anne'
};

console.log( obj1.getName() );     // 输出: sven
console.log( obj1.getName.call( obj2 ) );    // 输出：anne
```


### call 和 apply
ECAMScript 3 中给 Function 的原型定义的两个方法。

### 区别
传入参数形式的不同。具体区别如下：

apply 接受两个参数，第一个参数指定了函数体内 this 对象的指向，第二个参数为一个带下标的集合，这个集合可以是数组，也可以是类数组，apply 方法把这个集合中的元素作为参数传递给被调用的函数：
```JavaScript
var func = function( a, b, c ){
    alert ( [ a, b, c ] );    // 输出 [ 1, 2, 3 ]
};

func.apply( null, [ 1, 2, 3 ] );
```

call 传入的参数不固定，跟 apply 相同的是，第一个参数也是代表函数体内的 this 指向，从第二个参数开始往后，每个参数被一次传入函数：
```JavaScript
var func = function( a, b, c ){
    alert ( [ a, b, c ] );    // 输出 [ 1, 2, 3 ]
};

func.call( null, 1, 2, 3 );
```

### 如何选择使用 call 或 apply
	当调用一个函数时，JavaScript的解释器并不会计较形参和实参在数量、类型以及顺序上的区别，JavaScript的参数在内部就是用一个数组来表示的。从这个意义上说，apply比call的使用率更高，我们不必关心具体有多少参数被传入函数，只要用apply一股脑地推过去就可以了。
	call是包装在apply上面的一颗语法糖，如果我们明确地知道函数接受多少个参数，而且想一目了然地表达形参和实参的对应关系，那么也可以用call来传送参数。

### 用途

### 改变 this 指向
```JavaScript
var obj1 = {
    name: 'sven'
};

var obj2 = {
    name: 'anne'
};

window.name = 'window';

var getName = function(){
    alert ( this.name );
};

getName();    // 输出: window
getName.call( obj1 );    // 输出: sven
getName.call( obj2 );    // 输出: anne
```

### 使用 APPly 实现 bind 方法
[[Function.prototype.bind]]
