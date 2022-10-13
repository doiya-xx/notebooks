# Rust Programming Language

`rust`基于`c++`的一种语言，语法和`c++`类似，但是在内存管理有优势。也是一种预编译语言，需要使用`c++`的编译器。

## Install

### Windows

（1）存在两个版本，可以选择安装`MinGW/MSVC`

（2）下载`rustup-init.exe`。

下载地址：[https://www.rust-lang.org/zh-CN/tools/install](https://www.rust-lang.org/zh-CN/tools/install)

`rustup`是`rust`的环境版本管理工具。

（3）`rustup`自定义安装路径：

1. 创建存放 rust 环境目录`Rust/`；
2. 进入目录，创建`.cargo/`和`.rustup/`目录，这两个目录就是工具的安装路径；
3. 配置系统环境变量。创建两个系统环境变量`CARGO_HOME`和`RUSTUP_HOME`，两个系统环境变量的位置分别为第二步创建的两个目录。然后在`PATH`中添加`%CARGO_HOME%`和`%RUSTUP_HOME%`；
4. 启动`rustup-init.exe`，默认下载和使用 MSVC 版本的 rust。输入 3 选择使用 GNU 版本；
5. 然后输入 2，进行手动配置下载；
   1. 输入`x86_64-pc-windows-gnu`版本
   2. 输入`stable`版本
   3. 输入`complete`进行完整安装
   4. 输入`Y`允许修改系统环境变量
6. 最后输入 1 按照配置进行安装。

（4）检查

```shell
rustc --version
cargo --version
```

## Cargo

创建一个名为`project_name`的项目文件。

```shell
cargo new project_name
cd ./project_name # 进入项目目录
# 创建库
cargo new --lib restaurant
```

使用 debug 模式构建项目，生成 `project_name.exe`可执行文件。

```shell
cargo build
./target/debug/project_name.exe
```

使用 debug 模式构建并运行项目

```shell
cargo run
```

对项目进行构建，但是不生成可执行文件

```shell
cargo check
```

使用发布模式进行构建，生成的 `project_name.exe`运行速度更快。

```shell
cargo build --release
cargo run --release
```

更新项目依赖版本

```shell
cargo update
```

查看依赖 api 文档

```shell
cargo doc --open # 生成当前项目的依赖的api文档
```

一般使用 `vscode`或 `clion`进行编写，写好程序后，在 IDE 的终端里面输入 `cargo run`进行运行程序。

## Reference

官方英文文档地址：[https://www.rust-lang.org/](https://www.rust-lang.org/)

Rust Programming language: [https://doc.rust-lang.org/book/](https://doc.rust-lang.org/book/)

中文翻译版本文档地址：[https://www.rustwiki.org.cn/](https://www.rustwiki.org.cn/)

Rust 程序设计语言：[https://www.rustwiki.org.cn/zh-CN/book/](https://www.rustwiki.org.cn/zh-CN/book/)

Rust 圣经：[https://course.rs/about-book.html](https://course.rs/about-book.html)

## Rust

引入依赖。在 `Cargo.toml`中写入依赖以及版本，然后重新构建项目。

```toml
[dependencies]
rand = "0.8.5"
```

下载依赖

```shell
cargo build
```

区分语句和表达式的区别：

结尾没有分号的是表达式，函数是表达式。

代码块的返回值是最后一个表达式的值