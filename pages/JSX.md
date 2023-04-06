- ### 依赖下载
	- ```node
	  npm i @vitejs/plugin-vue-jsx -D
	  ```
- ### 具体使用
	- 安装完成之后在 vite.config.js 文件中的 plugins 字段中添加 jsx 支持：
	- ```javaScript
	  import vueJsx from "@vitejs/plugin-vue-jsx";
	  
	  export default defineConfig({
	    plugins: [
	      vueJsx(),
	    ]
	  })
	  ```