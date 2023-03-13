
示例代码如下：
```JavaScript
// 实现 bind 方法

Function.prototype.bind = function () {

	var self = this; // 保存原函数
	
	var context = Array.prototype.slice.call(arguments, 0, 1)[0]; // 保存需要绑定的this上下文
	
	var args = Array.prototype.slice.call(arguments, 1); // 剩余的参数转为数组
	
	return function () { // 返回一个新函数
	
	// 新函数传入的参数也转为数组
	
	var bindArgs = Array.prototype.slice.call(arguments);
	
		// 执行新的函数的时候，会把之前传入的 context 当作新函数运行时的 this，同时传入两次分别传入的参数，作为新函数的参数
	
	return self.apply(context, args.concat(bindArgs));
	
	}

}

var obj = {

	name: 'sven'

};

  

var func = function( a, b, c, d ){

	alert ( this.name ); // 输出：sven
	
	alert ( [ a, b, c, d ] ) // 输出：[ 1, 2, 3, 4 ]

}.bind( obj, 1, 2 );

  

func( 3, 4 );
```