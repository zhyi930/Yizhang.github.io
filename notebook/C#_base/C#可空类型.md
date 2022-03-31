# C# 可空类型

## 1 Nullable

C# 提供了一个特殊的数据类型，**nullable** 类型（可空类型），可空类型可以表示其基础值类型正常范围内的值，再加上一个 null 值。声明一个 **nullable** 类型（可空类型）的语法如下：

```c#
< data_type> ? <variable_name> = null;
```

##  2 单问号 ？

单问号用于对 **int、double、bool** 等无法直接赋值为 null 的数据类型进行 null 的赋值。

```c#
int? i = 3;
```

​	等同于：

```c#
Nullable<int> i = new Nullable<int>(3);
```

​	例：

```c#
double? d = new double?(1.0);	//正确写法
double d = new double(1.0);		//错误写法
```



## 3 双问号-Null合并运算符

Null 合并运算符用于定义可空类型和引用类型的默认值。Null 合并运算符为类型转换定义了一个预设值，以防可空类型的值为 Null。Null 合并运算符把操作数类型隐式转换为另一个可空（或不可空）的值类型的操作数的类型。如果第一个操作数的值为 null，则运算符返回第二个操作数的值，否则返回第一个操作数的值。

```c#
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
         
      static void Main(string[] args)
      {
         
         double? num1 = null;
         double? num2 = 3.14157;
         double num3;
         num3 = num1 ?? 5.34;      // num1 如果为空值则返回 5.34
         Console.WriteLine("num3 的值： {0}", num3);
         num3 = num2 ?? 5.34;
         Console.WriteLine("num3 的值： {0}", num3);
      }
   }
}
```

```
num3 的值： 5.34
num3 的值： 3.14157
```

## 4 单问号-条件表达式

和C++、Java中的条件表达式一样

```C#
b = (a == 1) ? 20 : 30;
```

如果a == 1，则b=20，否则b=30