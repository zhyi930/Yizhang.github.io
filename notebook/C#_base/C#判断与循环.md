# C# 判断与循环

## 1 switch判断

语法：

```c#
switch(expression){
    case constant-expression  :
       statement(s);
       break; 
    case constant-expression  :
       statement(s);
       break; 
    ......
    default : /* 可选的 */
       statement(s);
       break; 
}
```

- **switch** 语句中的 **expression** 必须是一个整型或枚举类型，或者是一个 class 类型，其中 class 有一个单一的转换函数将其转换为整型或枚举类型
- 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号
- case 的 **constant-expression** 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量
- 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 **break** 语句为止
- 当遇到 **break** 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行
- 不是每一个 case 都需要包含 **break**。如果 case 语句为空，则可以不包含 **break**，控制流将会 *继续* 后续的 case，直到遇到 break 为止
- C# 不允许从一个 case 部分继续执行到下一个 case 部分。如果 case 语句中有已经执行，则必须包含 **break** 或其他跳转语句
- 一个 **switch** 语句可以有一个可选的 **default** 语句，在 switch 的结尾。default 语句用于在上面所有 case 都不为 true 时执行的一个任务。default 也需要包含 **break** 语句，这是一个良好的习惯
- C# 不支持从一个 case 标签显式贯穿到另一个 case 标签。如果要使 C# 支持从一个 case 标签显式贯穿到另一个 case 标签，可以使用 goto 一个 switch-case 或 goto default

## 2 for each 循环

```c#
int[] fibarray = new int[] { 0, 1, 1, 2, 3, 5, 8, 13 };
foreach (int element in fibarray)
{
    System.Console.WriteLine(element);
}
```

