---
title: go语言笔记
date: 2020-07-07 10:30:00
---

1.如果自己实现的函数返回一个值和错误值，如果发生了错误，永远不要使用返回的值，他可能会使程序产生更多的错误，甚至奔溃。 // 标准库中的io.Reader.Read方法允许使用返回数据和错误。

2.如果main函数返回，整个程序也就终止了，程序终止时，还会关闭所有之前启动且还在运行的goroutine，所以写并发程序时，在main函数返回之前，清理并终止所有之前启动的goroutine，有助于减少bug，防止资源异常。

3.for range进行迭代数组、字符串、切片、映射和通道，使用for range迭代切片时，每次会返回两个值。第一个值是迭代元素在切片里的索引位置，第二个值是元素值的一个副本。如果函数返回多个值，而又不需要某个值时，可以使用下划线将其忽略。

```go
for _,feed := range feeds {
  
}
```

4.map是Go语言里的一个引用类型，需要使用make来构造。获取map中的值时，有两个选择，可以赋值给一个变量，也可以赋值给两个变量，赋值给两个变量时，第一个值和赋值给一个变量时一样，是map查找的结果值，第二个值会返回一个布尔值，来表示查找的键是否存在于map里，如果不存在，map会返回其值的零值作为返回值，如果这个键存在，map会返回所对应值的副本。
