`@while` 指令也可以用于循环样式，后面接 `SassScript` 表达式，循环会一直到表达式值为 `false` 时停止。

**示例：** 
循环遍历 `12px、14px、16px` 的字体样式：
```scss
$num: 12;
@while $num < 18 {
	.f-#{$num} {
		font-size: #{#num}px;
	}
	$num: $num + 2;
}
```

编译成 CSS 代码：

```css
.f-12 {
  font-size: 12px;
}

.f-14 {
  font-size: 14px;
}

.f-16 {
  font-size: 16px;
}
```

变量 `$num` 的初始值为 12 ，首先会输出 `font-size: 12px;` 然后每次循环会在原有的基础上加2，一直到不满足 `$num < 18` 这个条件，则循环停止。