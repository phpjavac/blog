# 数组和切片

## 数组

> 数组是一个长度固定的数据类型

```go
// 创建一个包含五个元素的整型数组 在golang中声明变量时，会使用对应类型的零值来进行初始化
var array [5]int // [0,0,0,0,0]
// 对数组初始化时可以指定每个元素的值
array := [5]int{1,2,3,4,5}
// 如果使用...来替代数组长度，会根据初始化时数组元素的数量来确定长度
array := [...]int{1,2,3,4,5}
// 初始数组时，可以给具体索引设置具体元素
array := 5[int]{1:2,2:3} // array -> [0,2,3,0,0]
```

修改数组索引的值```array[1] = 0```



## 切片

> 切片是围绕动态数组的概念构建的，可以按需自动增长或者缩小。

例子

```go
s := make([]int, 0, 3)
for i := 0; i < 5; i++ {
    s = append(s, i)
    fmt.Printf("cap %v, len %v, %p\n", cap(s), len(s), s)
}
```

将输出类似

```go
cap 3, len 1, 0x1040e130
cap 3, len 2, 0x1040e130
cap 3, len 3, 0x1040e130
cap 6, len 4, 0x10432220
cap 6, len 5, 0x10432220
```



### 创建

一种创建切面的方法是使用内置的make函数，还可以通过切面字面量来声明切片。

**使用切片字面量来创建切片时需注意，```[]string{"red","black"}``` 如果在[]运算符中制定了一个值，那么将创建数组而不是切片**

```go
// 创建一个字符串切片 长度和容量都是5
slice := make([]string,5)

// 如果只指定长度 那么切片的容量和长度相等，当然也可以分别制定长度和容量
slice := make([]string,2,5) // 创建一个长度为2个元素，容量为5个元素的切片
// 创建一个长度和容量都为0的空切片
slice := []string{}
```

### 使用



#### 赋值

对切片的索引赋值和对数组的赋值操作完全一样，使用[]操作符就可以改变某个元素的值。

```go
slice := []string{"red","black"}
slice[0] = "blue"
// slice ["blue","black"]
```

也可以对切片来创建切片

```go
slice := []int{1,2,3,4,5}
// 使用切片来创建切片，将得到一个 newSlice ->[2,3] 的切片，其长度和容量为2,4。
newSlice = slice[1:3]
```



#### 切片增长

> 对于数组来讲，使用切片的好处是可以按需增加切片的容量。其内部使用append函数来处理一切细节。

append方法，接受一个被操作的切片和一个要追加的值，返回一个增加后的新切片，append总是会增加新切片的长度，而容量有可能会改变，也有可能不会改变，取决于被操作的切片的可用容量

```go
// 创建一个容量长度都为5的整型切片
	slice := []int{1,2,3,4,5}
// 输出容量为5
	fmt.Println(cap(slice))
// 为切片增加一位值
	slice = append(slice,6)
// 输出slice cap 10 , 6 为切片追加元素后，如果长度超出容量，则容量小于1000时，总会成倍增加容量
// 一旦容量超过1000，则每次增加25%的容量
	fmt.Printf("slice cap %v , %v \n",cap(slice), len(slice));


	newSlice := make([]int,5,6)
	fmt.Println(cap(newSlice))
	newSlice = append(newSlice,6)
// 输出 6,6
	fmt.Printf("newSlice cap %v , %v \n",cap(newSlice), len(newSlice));
```

