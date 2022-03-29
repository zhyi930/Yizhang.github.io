# C# 简介

## 1 简介

​		**C#**是[微软](https://zh.wikipedia.org/wiki/微软)推出的一种基于[.NET框架](https://zh.wikipedia.org/wiki/.NET框架)的、[面向对象](https://zh.wikipedia.org/wiki/面向对象程序设计)的高级[编程语言](https://zh.wikipedia.org/wiki/编程语言)。C#是一种由C和C++派生出来的面向对象的编程语言。它在继承C和C++强大功能的同时去掉了一些它们的复杂特性，使其成为C语言家族中的一种高效强大的编程语言。C#以.NET框架类库作为基础，拥有类似[Visual Basic](https://zh.wikipedia.org/wiki/Visual_Basic)的快速开发能力。C#由[安德斯·海尔斯伯格](https://zh.wikipedia.org/wiki/安德斯·海尔斯伯格)主持开发，微软在2000年发布了这种语言，希望借助这种语言来取代[Java](https://zh.wikipedia.org/wiki/Java)。C#已经成为[Ecma国际](https://zh.wikipedia.org/wiki/Ecma国际)和[国际标准组织](https://zh.wikipedia.org/wiki/国际标准组织)的标准规范。

## 2 特征

* [指针](https://zh.wikipedia.org/wiki/指標)（Pointer）只能用于不安全模式之中。大多数对象访问透过安全的引用实现，以避免无效的调用，并且有许多算法用于验证溢出，指针只能用于调用值类型，以及受[垃圾收集](https://zh.wikipedia.org/wiki/垃圾回收_(計算機科學))控制的托管对象
* 对象不能被显式释放，代替为当不存在被引用时透过垃圾回收器回收
* 只允许[单一继承](https://zh.wikipedia.org/wiki/單一繼承)，但是一个类可以实现多个[接口](https://zh.wikipedia.org/wiki/接口)
* C#比C++更加[类型安全](https://zh.wikipedia.org/wiki/類型安全)。默认的安全转换是[隐含转换](https://zh.wikipedia.org/w/index.php?title=隱含轉換&action=edit&redlink=1)，例如由短整型转换为长整型和从派生类转换为基本类。而接口布尔型同整型，及枚举型同整型不允许隐含转换，非[空指针](https://zh.wikipedia.org/wiki/空指標)（透过引用相似对象）同用户定义类型的隐含转换字段被显式的确定，不同于C++的复制构造函数
* 数组声明语法不同（"int[] a = new int[5]"而不是"int a[5]"）
* [枚举](https://zh.wikipedia.org/wiki/枚举)位于其所在的[名字空间](https://zh.wikipedia.org/wiki/命名空间)中
* C#中没有[模版](https://zh.wikipedia.org/wiki/模板_(C%2B%2B))（Template），但是在C# 2.0中引入了[泛型](https://zh.wikipedia.org/wiki/泛型)（Generic programming），并且支持一些C++模版不支持的特性。比如泛型参数中的类型约束。另一方面，表达式不能像C++模版中被用于类型参数
* [属性](https://zh.wikipedia.org/wiki/属性)支持，使用类似访问成员的方式调用
* 完整的[反射](https://zh.wikipedia.org/wiki/反射式编程)支持

## 3 C# 编译器

* 最标准的C# 的实现当属[微软](https://zh.wikipedia.org/wiki/微軟)自己推出、并被包含在[.NET Framework](https://zh.wikipedia.org/wiki/.NET框架)内的C# 编译器
* 微软的Rotor项目（Rotor Project，目前称为[Shared Source Common Language Infrastructure](https://zh.wikipedia.org/w/index.php?title=Shared_Source_Common_Language_Infrastructure&action=edit&redlink=1)），提供了[通用语言运行库](https://zh.wikipedia.org/wiki/通用語言運行庫)（*Common Language Runtime*）的实现与C# 编译器。但是Shared Source Common Language Infrastructure在2006年的2.0版后就停止了
* 由Novell赞助的[Mono](https://zh.wikipedia.org/wiki/Mono) 项目提供了C# 编译器，同时也接近百分之百地实现了[.NET Framework](https://zh.wikipedia.org/wiki/.NET框架)类库。而Mono后来衍伸出由微软认可的第三方包[Xamarin](https://zh.wikipedia.org/wiki/Xamarin)
* [Dot GNU](https://zh.wikipedia.org/wiki/DotGNU) 项目也提供了另一个自由版本的C# 编译器，也提供了[.NET Framework](https://zh.wikipedia.org/wiki/.NET框架)类库的实现
* Borland提供了项目级的C# 集成开发环境，内部所使用的编译器仍是[微软](https://zh.wikipedia.org/wiki/微軟)[.NET Framework](https://zh.wikipedia.org/wiki/.NET框架)所提供的C# 编译器（这也意味着你仍须安装[微软](https://zh.wikipedia.org/wiki/微軟)的[.NET Framework](https://zh.wikipedia.org/wiki/.NET框架)）。产品：C# Builder（商业版本），Turbo C# Explorer（免费版本）

## 4 Hello World

```c#
using System;

namespace ConsoleApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

