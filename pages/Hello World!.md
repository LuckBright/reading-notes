### Hello World!
- 创建一个 **main.rs** 文件
- ```shell
  touch main.rs
  ```
- 编写 Rust 文件，一个打印 Hello，World！的程序。
- ```rust
  // A program that prints Hello, World!
  fn main() {
    // println! is a macro
    println!("Hello, world!");
  }
  ```
- 编译并运行文件：
- ```shell
  rustc main.rs
  ./main
  Hello，World！
  ```
- ![编译并运行程序](https://cdn.jsdelivr.net/gh/LuckBright/uPicImage@main/uPic/Eq59Fb.png)
- ### 编译和运行是彼此独立的步骤
- 在运行 **Rust** 程序之前，必须先试用 **Rust** 编辑器编译它，即输入 `rustc` 命令并传入源文件名称