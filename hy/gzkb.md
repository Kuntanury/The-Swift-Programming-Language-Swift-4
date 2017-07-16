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

用 `let` 声明常量，用 `var` 声明变量。常量在定义时不需要初始值，但是后续只能对它赋一次值。也就是说，你可以用常量来定义一个在很多地方用到的统一的值：

1. `var myVariable = 42`
2. `myVariable = 50`
3. `let myConstant = 42`

常量或变量的类型必须和赋值类型一样，然而，你却不需要写明类型，因为编译器可以根据你赋值的类型来推断他们类型：比如在上面的例子中， `myConstant` 初始化的值为整型数字，所以编译器推断 `myConstant` 的类型为整型。

如果初始化值未能提供足够的推断信息（或者没有初始值），可以显式的将类型写在变量的后面，用冒号与变量隔开：

1. `let implicitInteger = 70`
2. `let implicitDouble = 70.0`
3. `let explicitDouble: Double = 70`

> **小试身手**
>
> 创建一个显式类型为 **Float** 的值为 **4** 的常量。

值永远不会隐式转换为其他类型。如果你需要把一个值转换成不同类型，可以用显式类型转换来取得目标类型：

1. `let label = "The width is "`
2. `let width = 94`
3. `let widthLabel = label + String(width)`

> **小试身手**
>
> 尝试一下把最后一行的 String 类型转换去掉，看看编译器报什么错？

有一个更为简单的方法来将值转化为字符串——将值放在前面带有反斜线的括号 `\()` 里，如下所示：

1. `let apples = 3`
2. `let oranges = 5`
3. `let appleSummary = "I have \(apples) apples."`
4. `let fruitSummary = "I have \(apples + oranges) pieces of fruit."`

> **小试身手**
>
> 在一句欢迎语中用 `\()` 来把一个浮点运算结果转化为字符串并和某人的名字拼接起来
>
> `let greeting = "欢迎佳佳这个 \(3.0 - 1.0)货～"`

用三双引号 `"""` 来定义多行的字符串，每行字符的缩进都和结束的三双引号的缩进相同，如下所示（官方文档此处举例可能有问题，括号内及注释为个人理解所加，如有偏差，敬请指教）：

1. `let quotation = """`
2. （空格\)`Even though there's whitespace to the left, //即使左边有空白字符`
3. （空格\)`the actual lines aren't indented. //实际是不会包含在多行字符里面的`
4. （空格\)（空格\)`Except for this line. //除了这行`
5. （空格\)`Double quotes (") can appear without being escaped. //双引号可以不用转义`
6. ` `
7. （空格\)`I still have \(apples + oranges) pieces of fruit. //我还有几个苹果和橘子呢`
8. （空格\)`"""`

用方括号 `[]` 创建数组和字典，而访问的时候则是通过用方括号中写索引值或者键值的方式。最后一个元素后多加个逗号无碍：

1. `var shoppingList = ["catfish", "water", "tulips", "blue paint"]`
2. `shoppingList[1] = "bottle of water"`
3. `var occupations = [`
4. `"Malcolm": "Captain",`
5. `"Kaylee": "Mechanic",`
6. `]`
7. `occupations["Jayne"] = "Public Relations"`

用初始化语法创建一个空的数组或字典：

1. `let emptyArray = [String]()`
2. `let emptyDictionary = [String: Float]()`

如果元素类型可推导，你可以用 \[\] 初始化数组，用 \[:\] 初始化字典，就像你给变量赋值或者给函数传参数一样。

1. `shoppingList = []`
2. `occupations = [:]`

### 控制流程

---

`if` 和 `switch` 用来做条件判断， and use `for - in` ， `while` 和 `repeat - while` 用来做循环。判断条件和循环变量的圆括号可以省略，但是语句体的大括号不能：

1. `let individualScores = [75, 43, 103, 87, 12]`
2. `var teamScore = 0`
3. `for score in individualScores {`
4. `if score > 50 {`
5. `teamScore += 3`
6. `} else {`
7. `teamScore += 1`
8. `}`
9. `}`
10. `print(teamScore)`

在 if 语句中，判断条件必须是一个返回布尔值的表达式——也就是说  `if score { ... }` 这类写法是错误的，因为编译器不会隐式地与零值做比较。

你可以兼用 `if` 和 `let` 来处理赋值的变量可能为空的情况，这些赋值的变量表现为可选类型。可选类型或有确定值，或用 `nil` 来表示空值。在类型后添加 `?`  来表示变量为可选类型。

1. `var optionalString: String? = "Hello"`
2. `print(optionalString == nil)`
3. 4. `var optionalName: String? = "John APPleseed"`
5. `var greeting = "Hello!"`
6. `if let name = optionalName {`
7. `    greeting = "Hello, \(name)"`
8. `}`

> **小试身手**
>
> 把 `optionalName` 值改为 `nil` ， greeting输出什么？添加 `else` 分句：如果 `optionalName` 值为 `nil` 输出不同的greeting。

如果可选类型值为 nil ，由于判断条件为 false ，花括号中的代码就被跳过了。反之，可选类型的值就会被解包并赋给 let 声明的常量，这样，解包的值能够在花括号中可用了。

另一个处理可选类型值的方式是用 ?? 来提供一个默认值，如果可选类型值为空，就使用默认值。

1. `let nickName: String? = nil`
2. `let fullName: String = "John Appleseed"`
3. `let informalGreeting = "Hi \(nickName ?? fullName)"`

Switch语句支持任意数据类型的各种比较操作——不拘泥于整数及等式检测：

1. `let vegetable = "red pepper"`
2. `switch vegetable {`
3. `case "celery":`
4. `print("Add some raisins and make ants on a log.")`
5. `case "cucumber", "watercress":`
6. `print("That would make a good tea sandwich.")`
7. `case let x where x.hasSuffix("pepper"):`
8. `print("Is it a spicy\(x)?")`
9. `default:`
10. `print("Everything tastes good in soup.")`
11. `}`

> **小试身手**
>
> 把 `default` 结果删掉，看看报什么错？

留意一下上例中 `let` 的用法：通过将匹配式的值赋给常量的方式使得在判断分支中可以调用匹配式的值。

运行完 `switch` 语句中 `case` 匹配的代码后，程序就会结束整个选择。由于不在自动执行下一个判断，所以每个分支中的代码不需要加 `break` 来结束选择。

你可以 for-in 遍历代表键值对的一对值的方式来遍历字典。字典是无序的，所以遍历也是无序的。

1. `let interestingNumbers = [`
2. `"Prime": [2, 3, 5, 7, 11, 13],`

3. `"Fibonacci": [1, 1, 2, 3, 5, 8],`

4. `"Square"`  
   `: [`  
   `1`  
   `,`  
   `4`  
   `,`  
   `9`  
   `,`  
   `16`  
   `,`  
   `25`  
   `],`

5. `]`
6. `var`
   `largest`
   `=`
   `0`
7. `for`
   `(`
   `kind`
   `,`
   `numbers`
   `)`
   `in`
   `interestingNumbers`
   `{`
8. `for`
   `number`
   `in`
   `numbers`
   `{`
9. `if`
   `number`
   `>`
   `largest`
   `{`
10. `largest`
    `=`
    `number`
11. `}`
12. `}`
13. `}`
14. `print`
    `(`
    `largest`
    `)`

EXPERIMENT

Add another variable to keep track of which kind of number was the largest, as well as what that largest number was.

Use`while`to repeat a block of code until a condition changes. The condition of a loop can be at the end instead, ensuring that the loop is run at least once.

1. `var`
   `n`
   `=`
   `2`
2. `while`
   `n`
   `<`
   `100`
   `{`
3. `n`
   `*=`
   `2`
4. `}`
5. `print`
   `(`
   `n`
   `)`
6. 
7. `var`
   `m`
   `=`
   `2`
8. `repeat`
   `{`
9. `m`
   `*=`
   `2`
10. `}`
    `while`
    `m`
    `<`
    `100`
11. `print`
    `(`
    `m`
    `)`

You can keep an index in a loop by using`..<`to make a range of indexes.

1. `var`
   `total`
   `=`
   `0`
2. `for`
   `i`
   `in`
   `0`
   `..`
   `<`
   `4`
   `{`
3. `total`
   `+=`
   `i`
4. `}`
5. `print`
   `(`
   `total`
   `)`

Use`..<`to make a range that omits its upper value, and use`...`to make a range that includes both values.

