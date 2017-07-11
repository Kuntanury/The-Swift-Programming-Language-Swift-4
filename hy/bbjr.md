# 版本兼容

本书描述的是 Swift 4.0 版本，在 Xcode 9 中为 Swift 默认版本。你可以用Xcode 9来编译 Swift 3 或者 4 编写的代码。

> **备注**
>
> 当 Swfit 4 编译 Swift 3 代码时，会默认处理为3.2版本代码，这表示你可以用`#if swift(>=3.2)`这种判断条件来让代码兼容多个版本的 Swift 编译器

当你用 Xcode 9 编译 Swift 3 代码的时候， Swift 4 中的大部分功能也是可用的。只有如下功能是 Swift 4 代码独有的：

* 拆分字符串结果可以用 `Substring` 取代 `String` 类型

* `@objc` 修饰符可以在一些地方隐性调用

* 同一文件中类型的扩展可以访问当前类型中的私有成员

用 Swift 4 书写的 Target 可以依赖于 Swift 3 书写的 Target ，反之亦然。也就是说，如果你的工程分成了多个框架，你可以一个框架一个框架地从 Swift 3 迁移到 Swift 4 。

