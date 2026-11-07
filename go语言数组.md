# go语言数组

# 数组♥️

## 定义数组

```Go
var a [10]int
//var arrayname [size]datetype
//会初始化数组中元素的值
var a = [3]int{1,2,3}
//var arrayname [size]datetype{值}
a := [3]int{1,2,3}

var a = [...]int{1,2,3,4}
//不确定数组长度，用...代替数组长度，自动判定数组长度

var a = [...]int{2:66,0:33}
//这个意思是a[2]=66,a[0]=33,指定索引0
```

*索引超限会出错* 

## 二维数组

```Go
var arrayname [][]type
```

## 数组比较

```Go
a := [2][2]int{{1,2},{3,4}}
b := [2][2]int{{1,2},{3,4}}
c := [2][2]int{{1,1},{3,4}}

fmt.Println(a == b) -> true
fmt.Println(a == c) -> false
```

*数组长度是类型的一部分，不可以改变* 

# 切片

## 定义☀️

1. 声明未指定大小的数组来定义切片

```Go
var identifier []type
```

2. 使用make\(\)函数来创建切片

```Go
var slice1 []type = make([]type, len)
//等同于
slice1 := make([]type, len)
```

```Go
make([]T, length, capacity)
//T：容量  length：长度  capacity：容量
```

## 初始化☁

```Go
s :=[] int {1,2,3 } 
//[]表示是切片类型，{1,2,3}是初始化值
s := arr[start:end]
// 将 arr 中从下标 start 到 end-1 下的元素创建为一个新的切片
s := arr[start:]
//默认end时表示一直到最后一个元素
s := arr[:end]
//默认start时表示从第一个元素开始  
```

## len\( \)和cap\( \)函数🌲

- len\( \)可以获取数组长度

- cap\( \)可以获取数组容量

## 空\(nil\)切片

一个切片未初始化时默认为nil,长度为0

即切片 == nil 判断为真

len = 0,cap = 0

## append\( \)和copy\( \)函数🖊

```Go
a := []int

//向切片中添加一个元素0
a = append(a,0)

//添加多个元素
a = append(a,1,2,3)

//创建和a一样长度、容量的切片
b := make([]int, len(a),(cap(a)*2))

//拷贝a的内容到b
copy(a,b)
```

## 切片强制扩容🚪

1. 使用slices\.Grow

```Go
import "slices"

s := []int{1, 2, 3}
// 确保 s 至少有空间再放 5 个元素
s = slices.Grow(s, 5) 
// 此时 cap(s) >= len(s) + 5，但 len(s) 仍为 3
```

2. 显示创建新切片并复制

make一个新切片，再把旧数据copy过去

```Go
s := []int{1, 2, 3}
newCap := 100 // 你想要的目标容量

// 创建一个长度与原切片相同、但容量为 newCap 的新切片
t := make([]int, len(s), newCap)
copy(t, s)
s = t
```

3. 利用append扩容

使用append时一次追加超过容量的元素，强制扩容

# 作业📖😭

1. 给定s := make\(\[\]byte, 5\)，那么len\(s\) 和 cap\(s\) 分别是多少？令s = s\[2:4\]，len\(s\) 和 cap\(s\) 又分别是多少？

```Go
package main

import "fmt"

func main() {
    s := make([]int, 5, 10)
    fmt.Println(len(s), cap(s))  -> 5,10

    s = s[2:4]
    fmt.Println(len(s), cap(s))  -> 2,8
}
```

2. 比较**字符串**"hello，世界"的**长度**和for range该字符串的循环**次数**

```Go
package main

import "fmt"

func main() {
    a := "hello，世界"
    fmt.Println(len(a))  -> 14

    for i, v := range a {
        fmt.Printf("%-2d %2c %2d\n", i, v, v)
    }
    /* 0   h 104
     * 1   e 101
     * 2   l 108
     * 3   l 108
     * 4   o 111
     * 5   ， 65292
     * 8   世 19990
     * 11  界 30028*/
}
```







