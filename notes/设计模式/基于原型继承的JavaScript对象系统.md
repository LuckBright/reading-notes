	JavaScript语言是通过原型来构建一个面向对象的系统。

### 什么是原型模式？
	原型模式（prototype）是指用原型实例指向创建对象的种类，并且通过拷贝这些原型创建新的对象。 原型模式不单是一种设计模式，也被称为一种编程泛型。 从设计模式的角度讲，原型模式是用于创建对象的一种模式。

### 为什么对象是基于原型的面向对象系统？
	Brendan Eich 为 JavaScript 设计面向对象系统时，借鉴了 Self 和 Smalltalk 这两门基于原型的语言，为什么选择基于原型的面向对象系统呢，因为他一开始就没打算在 JavaScript 中加入类的概念。
	在原型编程的思想中，类并不是必须的，对象未必需要从类中创建而来，一个对象是通过克隆另外一个对象所得到的。

### 如何实现原型模式
原型模式的实现关键是语言本身是否提供了 `clone` 方法。

`ECMAScript 5 提供的 Object.create`
```javaScript
var Plane = function () {
	this.blood = 100;
	this.attackLevel = 1;
	this.defenseLevel = 1;
};

var plane = new Plane();
plane.blood = 500;
plane.attackLevel = 10;
plane.defenseLevel = 7;

var clonePlane = Object.create( plane );
console.log( clonePlane );   // 输出：Object {blood: 500, attackLevel: 10, defenseLevel: 7}

// Object.create 只是浅拷贝，如果改变 clonePlane 中 属性的值，目标值直接改变，而他的原型 prototype 上 blood 依旧不变。

```

	在不支持 Object.create 方法的浏览器中，可以使用如下代码：
```javaScript
Object.create = Object.create || function (obj) {
	var F = function() {};
	F.prototype = obj;
	return new F();
}
```

### 使用原型模式的目的？
JavaScript 中使用原型模式的主要目的是实现对象的代码重用和扩展，以提高代码的效率和可维护性。具体来说，使用原型模式可以带来以下几个优点：

1.  实现代码的重用：在 JavaScript 中，每个对象都有一个原型对象，通过在原型对象上定义属性和方法，可以实现对象之间的代码重用，避免在每个对象中都定义相同的属性和方法，从而减少代码的冗余。
    
2.  实现代码的扩展：由于原型对象是一个普通的对象，因此可以在运行时动态地向其添加属性和方法，从而实现对象的扩展。这种方式比使用类和继承等传统的面向对象编程方式更加灵活和易于实现。
    
3.  提高代码的性能：在 JavaScript 中，每个对象都有一个 **proto** 属性，它指向该对象的原型对象。在访问对象的属性和方法时，JavaScript 引擎会沿着原型链向上查找，如果找到了就返回该属性或方法，如果没有找到就继续沿着原型链查找。由于原型链是一条单向链，因此查找的效率比使用继承等方式更高。
    
4.  简化对象的创建：使用原型模式可以使对象的创建更加简单和快捷，只需要通过构造函数创建一个对象，并将其原型指向另一个对象即可。这种方式比使用类和继承等传统的面向对象编程方式更加简单和易于理解。
    

综上所述，使用原型模式可以使 JavaScript 中的对象更加灵活和易于维护，提高代码的效率和可扩展性，因此是 JavaScript 中常用的面向对象编程模式之一。