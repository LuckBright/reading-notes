- 所有的数据都是对象。
	- JavaScript中的根对象是 **Object.prototype** 对象。 **Object.prototype**  对象是一个空对象。在 JavaScript 中的所有对象，实际上都是从 **Object.prototype** 对象克隆而来，**Object.prototype**  对象就是它们的原型。
- 要得到一个对象，不是通过实例化类，而是找到一个对象作为原型并克隆它。
- 对象会记住它的原型。
- 如果对象无法响应某个请求，它会把这个请求委托给它自己的原型。