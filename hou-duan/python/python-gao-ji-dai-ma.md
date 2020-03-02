# Python高级代码

## 将函数作为参数

在python中，函数名也可以赋值给变量，并向c语言中的一样，函数也可以用来作为另一个函数的参数

```python
def add (x, y, i) :
    return f (x) f (y)
```

## Map 函数

`map（function，Iterator)`

map 函数可以接收一个函数和一个迭代器，然后将这个函数作用在迭代器各个元素上并返回一个新的迭代器。

## reduce 函数

`reduce(function，Iterator)`

reduce 函数接收一个函数和一个迭代器，使用前需要从 `functools` 中导入。

```python
from functools import reduce
```

`redune` 把一个函数作用在一个序列`[x1, x2, x3, ...]`上， 这个函数必须接收两个参数 `reduce` 把结果继续和序列的下一个元素做累计计算，其效果就是：

```python
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)
```

对一个序列求和，就可以用 `reduce` 实现：

```python
from functools import reduce
def add(x, y):
    return x + y

reduce(add, [1, 3, 5, 7, 9])
```

## 过滤器函数 filter

`filter(function, Iterator)`

filter 函数中第一个参数为函数，返回值必须为布尔值。

filter 会把函数作用在迭代器上面，并根据返回值决定是否要剔除迭代器中的一些元素。

