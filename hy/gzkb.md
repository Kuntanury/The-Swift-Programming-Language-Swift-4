# 管中窥豹

依照传统，使用新语言写的第一个程序都应该是在屏幕上打印 “Hello, world!” ，用 Swift ，一行搞定：

`print("Hello, world!")`

如果你曾经写过 C 或者 Objective-C 代码，那么你对 Swift 的语法不会感觉到陌生，在 Swift 中，上面的一行代码就是一个完整的程序，不需要引入单独的库或者I/O模块或者字符串处理神马的，因为写在全局范围的代码被当作程序的入口，所以你连 main\(\) 函数都省了，也不用在每句话结尾写分号了。

本节通过运用 Swfit 完成编程任务的方式，来让你 Swift 的有充足的了解。如果有什么地方不理解也不要担心——这个概览介绍的内容在本书的余下章节里都会进行详细解释的。

> **备注**
>
> 为了获得最佳体验，推荐用 Xcode 创建 playground 来试验本章内容，Playgrounds 允许你编辑代码并立即看到代码的运算结果。
>
> [下载Playground](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.playground.zip)

### 简单值

---

用 `let` 声明常量，用 `var` 声明变量。常量的值在编译时不需要初始化，但是你只能对它赋一次值。也就是说，你可以用常量来定义一个在很多地方用到的统一的值

Use`let`to make a constant and`var`to make a variable. The value of a constant doesn’t need to be known at compile time, but you must assign it a value exactly once. This means you can use constants to name a value that you determine once but use in many places.

1. `var myVariable = 42 `
2. `myVariable = 50 `
3. `let myConstant = 42 `

A constant or variable must have the same type as the value you want to assign to it. However, you don’t always have to write the type explicitly. Providing a value when you create a constant or variable lets the compiler infer its type. In the example above, the compiler infers that`myVariable`is an integer because its initial value is an integer.

