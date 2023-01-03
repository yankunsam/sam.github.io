---
title: "Go"
date: 2022-12-30T21:03:26+08:00
draft: true
---

## 取消一组任务

```
ctx,cancel := context.WithCancel(context.Background())

// 接受取消通知
<- ctx.Done()

```

## Interface

1. 在 build 阶段判断某 object 是否完整实现了 Interface 的 方法
```
type Reader interface {
	read()
}

type MyReader struct {
}

// 前后顺序很重要，定义一个 interface 类型的变量但不使用该变量（_），同时用实现该 interface 的类型的空值进行初始化
var _ Reader = (*MyReader)(nil)
```

## 方法

**本质**, 一个以 __方法所绑定类型实例__ 为第一个参数的  <span style="color:red">普通函数</span>

## for-range

### 数组
```
package main

import "fmt"

func main() {
	a := [5]int{1, 2, 3, 4, 5}
	r := make([]int, len(a))
	for i, v := range a {
		if i == 0 {
			a[1], a[2] = 12, 13
		}
		r[i] = v
	}
	fmt.Println("r", r)
	fmt.Println("a:", a)

}

```
输出结果如下
```
(base) sam:Desktop/ $ go run pid.go                                                                                                           [19:01:57]
r [1 2 3 4 5]
a: [1 12 13 4 5]
```

### Slice

```
package main

import "fmt"

func main() {
	a := []int{1, 2, 3, 4, 5}
	r := make([]int, len(a))
	for i, v := range a {
		if i == 0 {
			a[1], a[2] = 12, 13
		}
		r[i] = v
	}
	fmt.Println("r", r)
	fmt.Println("a:", a)

}

```
输出结果如下
```
(base) sam:Desktop/ $ go run pid.go                                                                                                           [19:04:26]
r [1 12 13 4 5]
a: [1 12 13 4 5]
(base) sam:Desktop/ $     
```