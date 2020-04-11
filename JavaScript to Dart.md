---
title: JavaScript to Dart
date: 2020-04-07 16:00:00
---

# JavaScript to Dart

## 主函数

Dart的入口函数必须为```main(）```，而JavaScript则没有预定义的入口函数。

``` Dart
// Dart 的入口文件
main() {
    print("hello word");
}
```

JavaScript

```JavaScript
// JavaScript则可以通过随便定义函数调用来执行为入口函数
function main(){
    console.log("hello word");
}
main();
```

## 变量

### 数据类型

Dart语言支持以下类型-

> Numbers

数值在Dart中有两种类型。

- Integer
     表示非小数值，即不带小数点的数字值。例如值"10"是整数。整数类型使用int关键字表示。
- Double
    Dart还支持浮点数数值，即带小数点的值。Dart中的Double数据类型表示64位（双精度）浮点数。例如，值"10.01"。关键字double用于表示浮点数类型。

> Strings

Dart 字符串是一组 UTF-16 单元序列。关键字String用于表示字符串文字。字符串通过单引号或者双引号创建。

> Booleans

布尔数据类型表示布尔值true和false。Dart使用bool关键字表示布尔值。

> List and Map

在Dart中创建list

```Dart
List<String> myList = List<String>(3);
myList[0] = 'one';
myList[1] = 'two';
myList[2] = 'three';
print(myList);
```

输出```Dart [one, two, three]```

在JavaScript中创建list

```JavaScript

const myList = new Array(3);
myList[0] = 'one';
myList[1] = 'two';
myList[2] = 'three';
console.log(myList);
```

输出```JavaScript [one, two, three]```

Dart Map是键值对的集合。它将每个键精确地映射到一个值。我们可以遍历一个Map。

在Dart中创建map

```Dart
import 'dart:collection';
HashMap map = HashMap<int, String>();
```

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。
在JavaScript中创建map

```JavaScript
const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"
```

## 创建变量

  在Dart中创建变量，变量类型必须是明确的或者是系统能够解析的类型，尽管类型是必需的，但某些类型注释是可选的，因为 Dart会执行类型推断。在JavaScript中则无法为变量指定类型。

```Dart
// Dart定义变量 需指定变量类型。
String name = "Tony";
int age = 18;
var name1 = "ergou"
```

```JavaScript
// 在js中 变量的类型则无法指定
let name = "Tony"
let age = 18
 ```

## 创建常量

  在Dart中创建常量，需使用final或const代替var。变量只能设置一次；const变量是编译时常量。实例变量可以是final但不能使用const。变量必须在构造函数开始前进行初始化。创建之后不可以修改常量的值。

```Dart
final name = 'Bob'; // Without a type annotation
final String nickname = 'Bobby';

const bar = 1000000;
const double atm = 1.01325 * bar; // Standard atmosphere
bar = 200000; // Error: Constant variables can't be assigned a value.
```

  在JavaScript中，const声明一个只读的常量。一旦声明，常量的值就不能改变。

```JavaScript
const name = "tom";
const age = 18;

age = 22; // Error: Assignment to constant variable.

```
