# C# 访问修饰符



## 1 分类

- [public](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/public)：同一程序集中的任何其他代码或引用该程序集的其他程序集都可以访问该类型或成员。 某一类型的公共成员的可访问性水平由该类型本身的可访问性级别控制。

- [private](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/private)：只有同一`class`或 `struct` 中的代码可以访问该类型或成员。

- [protected](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/protected)：只有同一 `class`或者从该 `class` 派生的 `class` 中的代码可以访问该类型或成员。

- [internal](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/internal)：同一程序集中的任何代码都可以访问该类型或成员，但其他程序集中的代码不可以。 换句话说，`internal` 类型或成员可以从属于同一编译的代码中访问。

- [protected internal](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/protected-internal)：该类型或成员可由对其进行声明的程序集或另一程序集中的派生 中的任何代码访问。

- [private protected](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/private-protected)：该类型或成员可以通过从 派生的类型访问，这些类型在其包含程序集中进行声明。

  |        调用位置        | public | protect internal | protected | internal | private protected | private |
  | :--------------------: | :----: | :--------------: | :-------: | -------- | ----------------- | ------- |
  |         在类内         |   ✔️️    |        ✔️️         |     ✔️️     | ✔️️        | ✔️️                 | ✔️️       |
  |  派生类（相同程序集）  |   ✔️️    |        ✔️️         |     ✔️️     | ✔️️        | ✔️️                 | ❌       |
  | 非派生类（相同程序集） |   ✔️️    |        ✔️️         |     ❌     | ✔️️        | ❌                 | ❌       |
  |  派生类（不同程序集）  |   ✔️️    |        ✔️️         |     ✔️️     | ❌        | ❌                 | ❌       |
  | 非派生类（不同程序集） |   ✔️️    |        ❌         |     ❌     | ❌        | ❌                 | ❌       |

## 2 可访问性

* 直接在命名空间中声明的类、普通数据类型和结构体可以为 `public` 或 `internal`。 如果未指定任何访问修饰符，则默认设置为 `internal`。

* 结构体的成员（包括嵌套的类和结构体）可以声明为 `public`、`internal` 或 `private`。

* 类的成员（包括嵌套的类和结构体）可以声明为 `public`、`protected internal`、`protected`、`internal`、`private protected` 或 `private`。

* 默认情况下，类成员和结构体成员（包括嵌套的类和结构体）的访问级别为 `private`。
