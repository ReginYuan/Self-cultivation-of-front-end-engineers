# 数组

JavaScript中，数组可以保存不同类型的值（但是尽量别这么做，大多数语言没有这个能力）

##### 数组的创建和初始化

```javascript
//用new的方式创建数组（并不是最好的方式）
var array = new Array()
var array = new Array(6)
var array = new Array('one','two','three')
//最佳创建方式
var array = []
```

#### 添加元素

```javascript
//假设有数组
var numbers = [0,1,2,3,4,5,6,7,8,9]
给数组添加一位元素，只要把值赋给数组的最后一个元素即可
numbers[numbers.length] = 10
```

- JS中，数组是可修改的对象，如果添加元素，它会动态增长
- 其他语言想添加元素就要创建全新的数组

> 通过push和pop，就能用数组来模拟栈

| push    | 将元素添加到数组的末尾 |
| ------- | ---------------------- |
| pop     | 将数组最后一位元素删除 |
| unshift | 将元素添加到数组的首位 |
| shift   | 将数组首位元素删除     |

> 通过shift和unshift，用数组模拟基本的队列

##### splice	在任意位置删除或添加元素

###### 删除

```javascript
.splice(起始索引,删除个数)
number.splice(5,3)	//从数组索引5开始的三个元素被删除
```

###### 添加

```javascript
.splice(起始索引,0,添加元素,添加元素...)
//第二个参数是删除元素的个数，为0时并传入第三个参数则表示添加元素
//第三个参数之后都是要添加的元素
```

##### concat	数组合并

> concat方法可以像一个数组传递数组、对象或是元素
>
> 数组会按照传入的参数顺序来合并出新数组

```javascript
var zero = 0
var positiveNumber = [1,2,3]
var negativeNumber = [-3,-2,-1]
var number = negtiveNumber.concat(zero,negativeNumber)
//number: -3、-2、-1、0、1、2、3
```

