- 什么是 Template ？
	- Template 是 Vue 中最常用的部分，它最终将 `DOM` 编译为 `rander` 函数，而它将模板转成 js 的过程，称之为模板编译。
- AST 又是什么？它和模板编译有什么关系？
	- 组件在渲染会前，会先进行 `模板编译`，将组件节点数据转换成 AST数据
	- 对整个数据进行监听
	- 监听完数据之后直接 render 函数，生成 vnode
- ![render函数渲染过程](https://cdn.jsdelivr.net/gh/LuckBright/uPicImage@main/uPic/VPMXiC.png)