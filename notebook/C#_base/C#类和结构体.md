# C# 类和结构体

## 1 成员

### 定义

类和结构体具有表示其数据和行为的成员。 类的成员包括在类中声明的所有成员，以及在该类的继承层次结构中的所有类中声明的所有成员（构造函数和析构函数除外）。 基类中的私有成员被继承，但不能从派生类访问。

### 成员类型

|                             成员                             | 描述                                                         |
| :----------------------------------------------------------: | :----------------------------------------------------------- |
| [字段](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/fields) | 字段是在类范围声明的变量。 字段可以是内置数值类型或其他类的实例。 例如，日历类可能具有一个包含当前日期的字段。 |
| [常量](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/constants) | 常量是在编译时设置其值并且不能更改其值的字段。               |
| [属性](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/properties) | 属性是类中可以像类中的字段一样访问的方法。 属性可以为类字段提供保护，以避免字段在对象不知道的情况下被更改。 |
| [方法](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/methods) | 方法定义类可以执行的操作。 方法可接受提供输入数据的参数，并可通过参数返回输出数据。 方法还可以不使用参数而直接返回值。 |
| [事件](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/events/) | 事件向其他对象提供有关发生的事情（如单击按钮或成功完成某个方法）的通知。 事件是使用委托定义和触发的。 |
| [运算符](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/) | 重载运算符被视为类型成员。 重载运算符时，将其定义为类型中的公共静态方法。 有关详细信息，请参阅[运算符重载](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/operator-overloading)。 |
| [索引器](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/indexers/) | 使用索引器可以用类似于数组的方式为对象建立索引。             |
| [构造函数](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/constructors) | 构造函数是首次创建对象时调用的方法。 它们通常用于初始化对象的数据。 |
| [终结器](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/finalizers) | C# 中很少使用终结器。 终结器是当对象即将从内存中移除时由运行时执行引擎调用的方法。 它们通常用来确保任何必须释放的资源都得到适当的处理。 |
| [嵌套类型](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/nested-types) | 嵌套类型是在其他类型中声明的类型。 嵌套类型通常用于描述仅由包含它们的类型使用的对象。 |

### 字段与属性

* 字段是在[类](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/class)或[结构体](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/struct)中直接声明的任意类型的变量，命名采取驼峰命名，住要是为类的内部做数据交互使用。当字段需要为外部提供数据的时候，请将字段封装为属性，而不是使用公有字段(public修饰符)，这是面向对象思想所提倡的。
* 属性是一种成员，它提供灵活的机制来读取、写入或计算私有字段的值。 属性可用作公共数据成员，但它们实际上是称为*访问器*的特殊方法。 这使得可以轻松访问数据，还有助于提高方法的安全性和灵活性。采用帕斯卡命名法。

```c#
using System;

class TimePeriod
{
   private double _seconds;

   public double Hours
   {
       get { return _seconds / 3600; }
       set {
          if (value < 0 || value > 24)
             throw new ArgumentOutOfRangeException(
                   $"{nameof(value)} must be between 0 and 24.");

          _seconds = value * 3600;
       }
   }
}

class Program
{
   static void Main()
   {
       TimePeriod t = new TimePeriod();
       // The property assignment causes the 'set' accessor to be called.
       t.Hours = 24;

       // Retrieving the property causes the 'get' accessor to be called.
       Console.WriteLine($"Time in hours: {t.Hours}");
   }
}
// The example displays the following output:
//    Time in hours: 24
```

## 2 抽象类与密封类

### 抽象类

通过在类定义前面放置关键字 `abstract`，可以将类声明为抽象类。 抽象类可以定义抽象方法。 方法是将关键字 `abstract` 添加到方法的返回类型的前面。抽象方法没有实现，所以方法定义后面是分号，而不是常规的方法块。 抽象类的派生类必须实现所有抽象方法。

```c#
public abstract class A
{
    public abstract void DoWork(int i);
}
```

### 密封类

通过在类定义前面放置关键字` sealed ` ，可以将类声明为[密封类](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/sealed)。密封类不能用作基类。 因此，它也不能是抽象类。 密封类禁止派生。 由于密封类从不用作基类，所以有些运行时优化可以略微提高密封类成员的调用速度。

## 3 静态类和静态类成员

[静态](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/static)类基本上与非静态类相同，但存在一个差异：静态类无法实例化。 换句话说，无法使用 [new](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/new-operator) 运算符创建类类型的变量。 由于不存在任何实例变量，因此可以使用类名本身访问静态类的成员。 例如，如果你具有一个静态类，该类名为 `UtilityClass`，并且具有一个名为 `MethodA` 的公共静态方法，如下面的示例所示：

```c#
UtilityClass.MethodA();
```

