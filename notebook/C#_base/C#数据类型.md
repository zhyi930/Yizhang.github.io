# C# 数据类型

## 1 分类

* 数值类型
* 引用类型
* 指针类型

## 2 值类型

|  类型   |                 描述                 |                          范围                           | 默认值 |
| :-----: | :----------------------------------: | :-----------------------------------------------------: | :----: |
|  bool   |                布尔值                |                      True 或 False                      | False  |
|  byte   |            8 位无符号整数            |                        0 到 255                         |   0    |
|  char   |          16 位 Unicode 字符          |                   U +0000 到 U +ffff                    |  '\0'  |
| decimal | 128 位精确的十进制值，28-29 有效位数 |         (-7.9 x 1028 到 7.9 x 1028) / 100 到 28         |  0.0M  |
| double  |          64 位双精度浮点型           |          (+/-)5.0 x 10-324 到 (+/-)1.7 x 10308          |  0.0D  |
|  float  |          32 位单精度浮点型           |               -3.4 x 1038 到 + 3.4 x 1038               |  0.0F  |
|   int   |         32 位有符号整数类型          |             -2,147,483,648 到 2,147,483,647             |   0    |
|  long   |         64 位有符号整数类型          | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 |   0L   |
|  sbyte  |          8 位有符号整数类型          |                       -128 到 127                       |   0    |
|  short  |         16 位有符号整数类型          |                    -32,768 到 32,767                    |   0    |
|  uint   |         32 位无符号整数类型          |                   0 到 4,294,967,295                    |   0    |
|  ulong  |         64 位无符号整数类型          |             0 到 18,446,744,073,709,551,615             |   0    |
| ushort  |         16 位无符号整数类型          |                       0 到 65,535                       |   0    |

## 3 引用类型

引用类型指的是内存中的地址，主要包含**object**、**dynamic** 和 **string**三种

#### 对象类型

​		**对象（Object）类型** 是 C# 通用类型系统（Common Type System - CTS）中所有数据类型的终极基类。Object 是 System.Object 类的别名。所以对象（Object）类型可以被分配任何其他类型（值类型、引用类型、预定义类型或用户自定义类型）的值。但是，在分配值之前，需要先进行类型转换。

#### 动态类型

​		可以存储任何类型的值在动态数据类型变量中。这些变量的类型检查是在运行时发生的。

```c#
dynamic d = 20;
```



#### 字符串类型

​		**字符串（String）类型** 允许您给变量分配任何字符串值。字符串（String）类型是 System.String 类的别名。它是从对象（Object）类型派生的。字符串（String）类型的值可以通过两种形式进行分配：引号和 @引号。C# string 字符串的前面可以加 @（称作"逐字字符串"）将转义字符（\）当作普通字符对待。@ 字符串中可以任意换行，换行符及缩进空格都计算在字符串长度之内。

```c#
string str = @"<script type=""text/javascript"">
    <!--
    -->
</script>";
```

## 4 指针类型

指针类型变量存储另一种类型的内存地址。C# 中的指针与 C 或 C++ 中的指针有相同的功能。

```c#
char* cptr;
int* iptr;
```

## 5 获取数据的存储空间

使用sizeof函数，单位为字节

```c#
using System;

namespace DataTypeApplication
{
   class Program
   {
      static void Main(string[] args)
      {
         Console.WriteLine("Size of int: {0}", sizeof(int));
      }
   }
}
```

## 6 类型转换

类型转换的形式：隐式转换、显式转换

#### 隐式转换

C# 默认的以安全方式进行的转换, 不会导致数据丢失。例如，从小的整数类型转换为大的整数类型，从派生类转换为基类

#### 显式转换

* 方法一

```c#
namespace TypeConversionApplication
{
    class ExplicitConversion
    {
        static void Main(string[] args)
        {
            double d = 5673.74;
            int i;
            // 强制转换 double 为 int
            i = (int)d;
            Console.WriteLine(i);
        }
    }
}
```

* 方法二

```c#
namespace TypeConversionApplication
{
    class StringConversion
    {
        static void Main(string[] args)
        {
            int i = 75;
            float f = 53.005f;
            double d = 2345.7652;
            bool b = true;

            Console.WriteLine(i.ToString());
            Console.WriteLine(f.ToString());
            Console.WriteLine(d.ToString());
            Console.WriteLine(b.ToString());         
        }
    }
}
```

| 序号 | 方法 & 描述                                                  |
| :--- | :----------------------------------------------------------- |
| 1    | **ToBoolean** 如果可能的话，把类型转换为布尔型。             |
| 2    | **ToByte** 把类型转换为字节类型。                            |
| 3    | **ToChar** 如果可能的话，把类型转换为单个 Unicode 字符类型。 |
| 4    | **ToDateTime** 把类型（整数或字符串类型）转换为 日期-时间 结构。 |
| 5    | **ToDecimal** 把浮点型或整数类型转换为十进制类型。           |
| 6    | **ToDouble** 把类型转换为双精度浮点型。                      |
| 7    | **ToInt16** 把类型转换为 16 位整数类型。                     |
| 8    | **ToInt32** 把类型转换为 32 位整数类型。                     |
| 9    | **ToInt64** 把类型转换为 64 位整数类型。                     |
| 10   | **ToSbyte** 把类型转换为有符号字节类型。                     |
| 11   | **ToSingle** 把类型转换为小浮点数类型。                      |
| 12   | **ToString** 把类型转换为字符串类型。                        |
| 13   | **ToType** 把类型转换为指定类型。                            |
| 14   | **ToUInt16** 把类型转换为 16 位无符号整数类型。              |
| 15   | **ToUInt32** 把类型转换为 32 位无符号整数类型。              |
| 16   | **ToUInt64** 把类型转换为 64 位无符号整数类型。              |