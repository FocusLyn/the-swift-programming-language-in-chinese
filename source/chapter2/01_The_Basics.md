# 基础部分

Swift 是 iOS 和 OS X 应用开发的一门新语言。然而，如果你有 C 或者 Objective-C 开发经验的话，你会发现 Swift 的很多内容都是你熟悉的。

Swift 的类型是在 C 和 Objective-C 的基础上提出的，`Int`是整型；`Double`和`Float`是浮点型；`Bool`是布尔型；`String`是字符串。Swift 还有两个有用的集合类型，`Array`和`Dictionary`，详情参见`集合类型(待添加链接)`。

就像 C 语言一样，Swift 使用变量来进行存储并通过变量名来关联值。在 Swift 中，值不可变的变量有着广泛的应用，它们就是常量，而且比 C 语言的常量更强大。在 Swift 中，如果你要处理的值不需要改变，那使用常量可以让你的代码更加安全并且更好地表达你的意图。

除了我们熟悉的类型，Swift 还增加了 Objective-C 中没有的类型比如元组（Tuple）。元组可以让你创建或者传递一组数据，比如作为函数的返回值时，你可以用一个元组可以返回多个值。

Swift 还增加了可选（Optional）类型，用于处理值缺失的情况。可选表示“那儿有一个值，并且它等于 x ”或者“那儿没有值”。可选有点像在 Objective-C 中使用`nil`，但是它可以用在任何类型上，不仅仅是类。可选类型比 Objective-C 中的`nil`指针更加安全也更具表现力，它是 Swift 许多强大特性的重要组成部分。

Swift 是一个类型安全的语言，可选就是一个很好的例子。Swift 可以让你清楚地知道值的类型。如果你的代码期望得到一个`String`，类型安全会阻止你不小心传入一个`Int`。你可以在开发阶段尽早发现并修正错误。

## 常量和变量

常量和变量把一个名字（比如`maximumNumberOfLoginAttempts`或者`welcomeMessage`）和一个指定类型的值（比如数字`10`或者字符串`Hello`）关联起来。常量的值一旦设定就不能改变，而变量的值可以随意更改。

### 声明常量和变量

常量和变量必须在使用前声明，用`let`来声明常量，用`var`来声明变量。下面的例子展示了如何用常量和变量来记录用户尝试登录的次数：

    let maximumNumberOfLoginAttempts = 10
    var currentLoginAttempt = 0

这两行代码可以被理解为
：
“声明一个名字是`maximumNumberOfLoginAttempts`的新常量，并给它一个值`10`。然后，声明一个名字是`currentLoginAttempt`的变量并将它的值初始化为0.”

在这个例子中，允许的最大尝试登录次数被声明为一个常量，因为这个值不会改变。当前尝试登录次数被声明为一个变量，因为每次尝试登录失败的时候都需要增加这个值。

你可以在一行中声明多个常量或者多个变量，用逗号隔开：

    var x = 0.0, y = 0.0, z = 0.0

> 注意：如果你的代码中有不需要改变的值，请将它声明为常量。只将需要改变的值声明为变量。

### 类型标注

当你声明常量或者变量的时候可以加上类型标注，说明常量或者变量中要存储的值的类型。如果要添加类型标注，在常量或者变量名后面加上一个冒号和空格，然后加上类型名称。

这个例子给`welcomeMessage`变量添加了类型标注，表示这个变量可以存储`String`类型的值：

    var welcomeMessage: String

声明中的冒号代表着“是...类型”，所以这行代码可以被理解为：：

“声明一个类型为`String`，名字为`welcomeMessage`的变量。”

“类型为`String`”的意思是“可以存储任意`String`类型的值。”

`welcomeMessage`变量现在可以被设置成任意字符串：

    welcomeMessage = "Hello"

> 注意：一般来说你很少需要写类型标注。如果你在声明常量或者变量的时候赋了一个初始值，Swift可以推断出这个常量或者变量的类型，详情参见`类型安全和类型推断(待添加链接)`。在上面的例子中，没有给`welcomeMessage`赋初始值，所以添加了一个类型标注。

### 常量和变量的命名

你可以用任何你喜欢的字符作为常量和变量名，包括Unicode字符：

        let π = 3.14159
        let 你好 = "你好世界"
        let 🐶🐮 = "dogcow"

常量与变量名不能包含数学符号，箭头，保留的(或者非法的)Unicode码位，连线与制表符。尽管常量与变量名中可以包含数字，但是它们不能以数字打头。

一旦你将常量或者变量声明为确定的类型，你就不能使用相同的名字再次进行声明，或者以改变其存储的值为其他类型。同时，你也不能将常量与变量进行互转。

> 注意：如果你需要使用与Swift保留关键字相同的名称作为常量或者变量名，你可以使用反引号(`)将关键字围住的方式将其作为名字使用。无论如何，你应当避免使用关键字作为常量或变量名，除非你别无选择。

你可以更改现有的变量值为其他同类型的值，在下面的例子中，`friendlyWelcome`的值从`"Hello!"`改为了`"Bonjour!"`:

        var friendlyWelcome = "Hello!"
        friendlyWelcome = "Bonjour!"
        // friendlyWelcome is now "Bonjour!"

和变量不一样，常量的值一旦被确定以后就不能更改了。尝试这样做会在编译时报错：

        let languageName = "Swift"
        languageName = "Swift++"
        // this is a compile-time error - languageName cannot be changed

### 输出常量和变量

你可以用`println`函数来输出当前常量或变量的值:

        println(friendlyWelcome)
        // prints "Bonjour!"

`println`是一个用来输出的全局函数，输出的内容会在最后带换行。如果你用Xcode，`println`将会输出内容到“console”面板上。(另一种函数叫`print`，唯一区别是在输出内容最后不会加入换行。)

`println`函数输出传入的`String`值：

        println("This is a string")
        // prints "This is a string"

像Cocoa里的`NSLog`函数一样，`println`函数可以输出更复杂的信息。这些信息可以包含当前常量和变量的值。

Swift用字符串插值（string interpolation）的方式把常量名或者变量名当做占位符加入到长字符串中，Swift会用当前常量或变量的值替换这些占位符。将常量或变量名放入反斜杠符加一对圆括号中`"\()"`：

        println("The current value of friendlyWelcome is \(friendlyWelcome)")
        // prints "The current value of friendlyWelcome is Bonjour!

> 注意：字符串插值所有可用的选项在 字符串插值 这章中讲述。

### 注释
请将你的代码中的非执行文本注释成提示或者笔记以方便你将来阅读。Swift 的编译器将会在编译代码时自动忽略掉注释部分。

Swift 中的注释与C 语言的注释非常相似。单行注释以双正斜杠作(//)为起始标记:

	// this is a comment

你也可以进行多行注释，其起始标记为单个正斜杠后跟随一个星号(/\*)，终止标记为一个星号后跟随单个正斜杠(\*/):

	/* this is also a comment,
	but written over multiple lines */

与C 语言多行注释不同的是，Swift 的多行注释可以嵌套在其它的多行注释之中。你可以先生成一个多行注释块，然后在这个注释块之中再嵌套成第二个多行注释。终止注释时先插入第二个注释块的终止标记，然后再插入第一个注释块的终止标记：

	/* this is the start of the first multiline comment
	/* this is the second, nested multiline comment */
	this is the end of the first multiline comment */

通过运用嵌套多行注释，你可以快速方便的注释掉一大段代码，即使这段代码之中已经含有了多行注释块。

## 分号
与其他大部分编程语言不同，Swift 并不强制要求你在每条语句的结尾处使用分号(;)，当然，你也可以按照你自己的习惯添加分号。有一种情况下必须要用分号，即你打算在同一行内写多条独立的语句:

	let cat = "🐱"; println(cat)
	// prints "🐱"


## 整数

整数就是没有小数部分的数字，比如`42`和`-23`。整数可以是有符号（正、负、零）或者无符号（正、零）。

Swift 提供了8、16、32和64位的有符号和无符号整数类型。这些整数类型和 C 语言的命名方式很像，比如8位无符号整数类型是`UInt8`，32位有符号整数类型是`Int32`。就像 Swift 的其他类型一样，整数类型采用大写命名法。

### 整数范围

你可以访问不同整数类型的`min`和`max`属性来获取对应类型的最大值和最小值：

    let minValue = UInt8.min  // minValue 为 0，是 UInt8 类型的最小值
    let maxValue = UInt8.max  // maxValue 为 255，是 UInt8 类型的最大值

### Int

一般来说，你不需要专门指定整数的长度。Swift 提供了一个特殊的整数类型`Int`，长度与当前平台的原生字长相同：

* 在32位平台上，`Int`和`Int32`长度相同。
* 在64位平台上，`Int`和`Int64`长度相同。

除非你需要特定长度的整数，一般来说使用`Int`就够了。这可以提高代码一致性和可复用性。即使是在32位平台上，`Int`可以存储的整数范围也可以达到`-2147483648`~`2147483647`，大多数时候这已经足够大了。

### UInt

Swift 也提供了一个特殊的无符号类型`UInt`，长度与当前平台的原生字长相同：

* 在32位平台上，`UInt`和`UInt32`长度相同。
* 在64位平台上，`UInt`和`UInt64`长度相同。

> 注意：尽量不要使用`UInt`，除非你真的需要存储一个和当前平台原生字长相同的无符号整数。除了这种情况，最好使用`Int`，即使你要存储的值已知是非负的。统一使用`Int`可以提高代码的可复用性，避免不同类型数字之间的转换，并且匹配数字的类型推测，详情参见[类型安全和类型推测](## 类型安全和类型推测)。

## 浮点数

浮点数是有小数部分的数字，比如`3.14159`，`0.1`和`-273.15`。

浮点类型比整数类型表示的范围更大，可以存储比`Int`类型更大或者更小的数字。Swift 提供了两种有符号浮点数类型：

* `Double`表示64位浮点数。当你需要存储很大或者很高精度的浮点数时请使用此类型。
* `Float`表示32位浮点数。精度要求不高的话可以使用此类型。

> 注意：`Double`精确度很高，至少有15位数字，而`Float`最少只有6位数字。选择哪个类型取决于你的代码需要处理的数字大小。

## 类型安全和类型推测

Swift 是一个类型安全的语言。类型安全的语言可以让你清楚地知道代码要处理的值的类型。如果你的代码需要一个`String`，你绝对不可能不小心传进去一个`Int`。

Swift 是类型安全的，会在编译你的代码时进行类型检查，如果遇到不匹配的类型会报错。这可以让你在开发的时候尽早发现并修复错误。

当你要处理不同类型的值时，类型检查可以帮你避免错误。然而，这并不是说你每次声明常量和变量的时候都需要显式指定类型。如果你没有显式指定类型，Swift 会使用类型推测来选择合适的类型。有了类型推测，编译器可以在编译代码的时候自动推测出表达式的类型。原理很简单，判断你赋的值即可。

因为有类型推测，和 C 或者 Objc 比起来 Swift 很少需要声明类型。常量和变量虽然需要明确类型，但是大部分工作并不需要你自己来完成。

当你声明常量或者变量并赋初值的时候类型推测非常有用。当你在声明常量或者变量的时候赋给它们一个原始值即可触发类型推测。（原始值就是会直接出现在你代码中的值，比如`42`和`3.14159`。）

举个例子，如果你给一个新常量赋值`42`并且没有标明类型，Swift 可以推测出常量类型是`Int`，因为你给它赋的初值看起来很像一个整数：

    let meaningOfLife = 42
    // meaningOfLife 会被推测为 Int 类型

同理，如果你没有给浮点原始值标明类型，Swift 会推测你想要的是`Double`：

    let pi = 3.14159
    // pi 会被推测为 Double 类型

当推测浮点数的类型时，Swift 总是会选择`Double`而不是`Float`。

如果表达式中同时出现了整数和浮点数，会被推测为`Double`类型：

    let anotherPi = 3 + 0.14159
    // anotherPi 会被推测为 Double 类型

原始值`3`没有显式声明类型，而表达式中出现了一个浮点原始值，所以表达式会被推测为`Double`类型。

## 数值类原始值

整数原始值可以被写作：

* 一个十进制数，没有前缀
* 一个二进制数，前缀是`0b`
* 一个八进制数，前缀是`0o`
* 一个十六进制数，前缀是`0x`

下面的所有整数原始值的十进制值都是`17`:

    let decimalInteger = 17
    let binaryInteger = 0b10001       // 二进制的17
    let octalInteger = 0o21           // 八进制的17
    let hexadecimalInteger = 0x11     // 十六机制的17

浮点原始值可以是十进制（没有前缀）或者是十六进制（前缀是`0x`）。小数点两边必须有至少一个十进制数字（或者是十六进制的数字）。浮点原始值还有一个可选的指数，在十进制浮点数中通过大写或者小写的`e`来指定，在十六进制浮点数中通过大写或者小写的`p`来指定。

如果一个十进制数的指数为`exp`，那这个数相当于基数和10^exp的乘积：
* 1.25e2 表示 1.25 × 10^2，等于 125.0。
* 1.25e-2 表示 1.25 × 10^-2，等于 0.0125。

如果一个十六进制数的指数为`exp`，那这个数相当于基数和2^exp的乘积：
* 0xFp2 表示 15 × 2^2，等于 60.0。
* 0xFp-2 表示 15 × 2^-2，等于 3.75。

下面的这些浮点原始值都等于十进制的`12.1875`：

    let decimalDouble = 12.1875
    let exponentDouble = 1.21875e1
    let hexadecimalDouble = 0xC.3p0

数值类原始值可以包括额外的格式来增强可读性。整数和浮点数都可以添加额外的零并且包含下划线，并不会影响原始值：

    let paddedDouble = 000123.456
    let oneMillion = 1_000_000
    let justOverOneMillion = 1_000_000.000_000_1

## 数值类型转换

通常来讲，即使代码中的整数常量和变量已知非负，也请使用`Int`类型。总是使用默认的整数类型可以保证你的整数常量和变量可以直接被复用并且可以匹配整数类原始值的类型推测。
只有在必要的时候才使用其他整数类型，比如要处理外部的长度明确的数据或者为了优化性能、内存占用等等。使用显式指定长度的类型可以及时发现值溢出并且可以暗示正在处理特殊数据。

### 整数转换

不同整数类型的变量和常量可以存储不同大小的数字。`Int8`类型的常量或者变量可以存储的数字范围是`-128`~`127`，`UInt8`类型的常量或者变量能存储的数字范围是`0`~`255`。如果数字超出了常量或者变量可存储的范围，编译的时候会报错：

    let cannotBeNegative: UInt8 = -1
    // UInt8 类型不能存储负数，所以会报错
    let tooBig: Int8 = Int8.max + 1
    // Int8 类型不能存储超过最大值的数，所以会报错

因为每一个整数类型都可以存储不同范围的值，你必须根据情况来选择不同的转换方法。不同的转换方法可以暴露出隐藏的转换错误并让你的代码更加清晰。

要将一种数字类型转换成另一种，你要用当前值来初始化一个新数字，这个数字的类型就是你的目标类型。在下面的例子中，常量`twoThousand`类型是`UInt16`，然而常量`one`类型是`Uint8`。它们不能直接相加，因为它们类型不同。所以要调用`UInt16(one)`来创建一个新的`UInt16`数字并用`one`的值来初始化，然后使用这个新数字来计算：

    let twoThousand: UInt16 = 2_000
    let one: UInt8 = 1
    let twoThousandAndOne = twoThousand + UInt16(one)

现在两个数字的类型都是`UInt16`，可以进行相加。目标常量`twoThousandAndOne`的类型被推测为`UInt16`，因为它是两个`UInt16`值的合。

`SomeType(ofInitialValue)`是调用 Swift 构造器并传入一个初始值的默认方法。在语言内部，`UInt16`有一个构造器，可以接受一个`UInt8`类型的值，所以这个构造器可以用现有的`UInt8`来创建一个新的`UInt16`。注意，你并不能传入任意类型的值，只能传入`UInt16`内部有对应构造器的值。不过你可以扩展现有的类型来让它可以接收其他类型的值（包括自定义类型），详情参见`扩展(链接待添加)`.

### 整数和浮点数转换

整数和浮点数的转换必须显式指定类型：

    let three = 3
    let pointOneFourOneFiveNine = 0.14159
    let pi = Double(three) + pointOneFourOneFiveNine
    // pi 等于 3.14159，所以被推测为 Double 类型

这个例子中，常量`three`的值被用来创建一个`Double`类型的值，所以加号两边的数类型相同。如果不进行转换，两者无法相加。

浮点数转换为整数也一样，整数类型可以用`Double`或者`Float`类型来初始化：

    let integerPi = Int(pi)
    // integerPi 等于 3，所以被推测为 Int 类型

当用这种方式来初始化一个新的整数值时，浮点值会被截断。也就是说`4.75`会变成`4`，`-3.9`会变成`3`。

> 注意：结合数字类常量和变量不同于结合数字类原始值。原始值`3`可以直接和原始值`0.14159`相加，因为数字原始值本身没有明确的类型。它们的类型只在编译器需要求值的时候被推测。

