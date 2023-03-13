实际业务中经常有需要我们处理输入框的限制输入数字小数点后几位，具体实现如下:
```html
<input v-model="inputNum" @input="handleInputChange"/>

<script>
let inputNum = ''

// 限制为小数点后几位
const MATCH_NUM = /^\d*(\.\d{0,2})?/
// 判断是否为数字，且第一位不能为小数点
const isNum = /^[0-9]+(\.[0-9]{0,2})?$/
const handleInputChange = (event) => {
	let val = event.target.value
	if (!isNum.test(val)) {
		// 阻止默认事件
		event.preventDefault()
		// 开头第一位如果是小数点就在前面补上0，否则祛除多余的文字
		val = val[0] === '.' ? '0.' : val.replace(/[^\d.]/g, '')
	}
	val = val.match(MATCH_NUM)[0]

	this.inputNum = val
}
</script>

```