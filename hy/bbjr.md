# 版本兼容

本书描述的是Swift4.0版本，在Xcode 9中为Swift默认版本。你可以用Xcode 9来编译Swift 3或者4编写的代码。

> **备注**
>
> 当Swfit 4编译Swift 3代码时，会默认处理为3.2版本代码，这表示你可以用`#if swift(>=3.2)`这种判断条件来让代码兼容多个版本的Swift编译器

When you use Xcode 9 to build Swift 3 code, most of the new Swift 4 functionality is available. That said, the following features are available only to Swift 4 code:

* Substring operations return an instance of the`Substring`type, instead of`String`.

* The`@objc`attribute is implicitly added in fewer places.

* Extensions to a type in the same file can access that type’s private members.

A target written in Swift 4 can depend on a target that’s written using Swift 3, and vice versa. This means, if you have a large project that is divided into multiple frameworks, you can migrate your code from Swift 3 to Swift 4 one framework at a time.

