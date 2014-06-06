# 基本类型

Swift是iOS和OS X开发使用的一门新语言. 尽管如此, Swift中还是有很多部分和使用C、Objective-C开发时的体验很相似.

Swift提供了所有C和Objective-C中重要的类型, 包括<code>Int</code>(整数), <code>Double</code>和<code>Float</code>(浮点数), <code>Bool</code>(布尔值), <code>String</code>(文本). Swift提供了两个强大的集合类型, <code>Dictionary</code>和<code>Array</code>, 具体请参见[Collection Types]().

跟C一样, Swift通过一个指定的名称使用变量来存储和代表某些值. Swift中大量运用了那些值不可变的变量, 称作常量. 常量比在C中更强大, 它在Swift中贯穿始终来保证代码更加安全, 更加简洁.

除了我们熟悉的类型, Swift引入了Objective-C中没有的高级类型, 这就包括元组(可以创建和传递一组值), 它可以作为一个复合值从函数中返回.

Swift还引入了可选类型用来处理未知值. 可选类型的意思是"要么存在一个值, 要么根本没有值". 可选类型和Objective-C中使用指针时的<code>nil</code>很相似, 但是它适用任何类型, 不仅仅是类. 可选类型比<code>nil</code>更加安全明了, 是许多Swift强大功能的核心.

可选类型表明Swift是一个**强类型**语言. Swift帮助你明确每个值的类型. 如果你的代码希望得到传入一个<code>String</code>类型, 类型安全机制会防止你误传入一个<code>Int</code>类型. 这可以帮助你在开发过程中尽可能的捕捉和修复错误.

### 常量与变量

常量和变量把特定类型的值(如数字<code>10</code>或字符串<code>"hello"</code>)与一个名称(如<code>maximumNumberOfLoginAttempts</code>或<code>welcomeMessage</code>)联系在一起. **常量**的值一旦被设定就不能更改, 然而**变量**在后面可以被设置为一个不同的值.

### 声明常量与变量

常量与变量在使用之前必须被声明. 使用<code>let</code>关键字声明常量, <code>var</code>关键词声明变量. 举个栗子, 下面是关于如何使用常量和变量来追踪用户的登录尝试次数的代码:

```javascript
let maximumNumberOfLoginAttempts = 10
var currentLoginAttempt = 0
```

这段代码可以这样理解:

"声明一个常量叫做<code>maximumNumberOfLoginAttemps</code>, 赋值为10. 然后声明一个变量叫做<code>currentLoginAttempt</code>, 初始值为0."

在这个栗子中, 允许登录的最大尝试次数被声明为常量, 因为最大值永远不变. 当前尝试次数被声明为变量, 因为这个值在每次登录失败后会增加.

你可以在同一行上声明多个常量或变量, 以逗号分隔:

```javascript
var x=0.0, y=0.0, z=0.0
```

> 如果代码中的值不会变化, 请使用<code>let</code>关键字声明为常量. 只有存储的值需要变化的时候才使用变量.

类型注解

在声明常量或变量的时候, 你可以添加一个**类型注解**来表明这个常量或变量能存储什么样的值. 语法格式是: 在变量或常量后面添加冒号, 然后空格, 然后是类型名称.

下面这个栗子为一个叫做<code>welcomeMessage</code>的变量进行类型注解, 表明这个变量只能存储<code>String</code>类型:

```javascript
var welcomeMessage: String
```

冒号的意思是"xx类型的...", 所以上面的代码可以这么理解:

"声明一个<code>String</code>类型的变量叫<code>welcomeMessage</code>."

这句话中"<code>String</code>类型的"是指"能存储任何<code>String</code>类型的值".

<code>welcomeMessage</code>变量现在可以被设置为任何的字符串:

```javascript
welcomeMessage = "Hello"
```

> 在实际中你很少需要写类型注解. 如果你在一个常量或变量被定义的时候设置初始值, Swift通常会自己判断那个常量或变量的类型, 具体请参见[Type Safety and Type Inference](). 在上述<code>welcomeMessage</code>栗子中, 没有设置任何初始值, 所以<code>welcomeMessage</code>变量的类型通过类型注解指定而不是通过初始值判定.

### 命名常量和变量

你可以用大部分你喜欢的字符来命名常量和变量, 包括Unicode字符:

```javascript
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```

常量和变量不能包含任何数学符号, 箭头, 私有(或无效)Unicode字符, 或制表符, 也不能以数字开头, 虽然数字可以在其他地方出现.

一旦你声明了一个特定类型的常量或变量, 你不能以相同的名字再次声明或是改变它的类型, 也不能将常量变为变量, 变量变为常量.

> 如果你想要用Swift保留关键字给常量或变量命名, 你可以用<code>`</code>包围关键字. 但是, 不到万不得已, 还是不要这样的好.

你可以改变一个已存在的变量的值. 在下面这个栗子中, <code>friendlyWelcome</code>的值从<code>"Hello!"</code>变成了<code>"Bonjour!"</code>:

```javascript
var friendlyWelcome = "Hello!"
friendlyWelcome = "Bonjour!"
// friendlyWelcome 现在是 "Bonjour!"
```

常量则不一样, 它的值一旦设置就不能改变. 非要尝试改变的话, 编译的时候会报错:

```javascript
let languageName = "Swift"
languageName = "Swift++"
// 这是一个编译错误 - languageName不能被改变
```

### 打印常量与变量

你可以用<code>println</code>打印常量和变量的值:

```javascript
println(friendlyWelcom)
// 打印 "Bonjour!"
```

<code>println</code>函数能打印更多负责的日志消息, 与Cocoa的<code>NSLog</code>相似. 这些消息可以包含常量和变量.

Swift使用**字符串插入**










