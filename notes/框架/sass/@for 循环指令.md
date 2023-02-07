`@for` 指令可以用于循环生成样式， `for` 指令有两种类型，如下所示：
```javaScript
// 第一种
@for $var from <start> through <end>

// 第二种
@for $var from <start> to <end>
```

其中 `$var`  表示变量， `start` 表示循环的起始值，`end` 表示结束值。而这这两种方式的区别就在于 关键字 `through` 会包含 `end` 这个次数，而 `to` 不包含。

**示例：** 
如下代码，使用 `through` 关键字实现循环:
```scss
@for $var from 1 through 3 {
	.width#{$var} {
		width: $var * 10px;
	}
}
```

编译后结果：
```css
.width1 {
  width: 10px;
}

.width2 {
  width: 20px;
}

.width3 {
  width: 30px;
}
```

如下代码，使用 `to` 关键字实现循环:
```scss
@for $var from 1 to 3 {
	.width#{$var} {
		width: $var * 10px;
	}
}
```

编译后结果：
```css
.width1 {
  width: 10px;
}

.width2 {
  width: 20px;
}
```