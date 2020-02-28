# MarkDown 语法归纳

## 标题

使用 `#` 来作为标题

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

大标题为一级，其次是二级，以此类推，尽量不要跳级。

应尽量控制用到三级。

## 文本

每个段落之间需要空出一行代表换行。

对文本拥有以下操作方法：

```markdown
*斜体文本*

_斜体文本_

**粗体文本**

__粗体文本__

***粗斜体文本***

___粗斜体文本___

~~删除文本~~

<u>下划线文本</u>
```

演示：


*斜体文本*

_斜体文本_

**粗体文本**

__粗体文本__

***粗斜体文本***

___粗斜体文本___

~~删除文本~~

<u>下划线文本</u>

## 分割线

```markdown

***

* * *

*****

- - -

----------

```

演示：

***

* * *

*****

- - -

----------

## 列表

### 无序列表

使用 `-` 或者 `*`

```markdown
- Apple
- Banana
- Pear
- vegetable
  - Tomato
  - Potato

* Apple
* Banana
* Pear
* vegetable
  * Tomato
  * Potato
```

演示：

- Apple
- Banana
- Pear
- vegetable
  - Tomato
  - Potato

* Apple
* Banana
* Pear
* vegetable
  * Tomato
  * Potato

### 有序列表

使用 `1. 2. 3.`

```markdown
1. Apple
2. Banana
3. Pear
4. vegetable
  - Tomato
  - Potato

```

演示：

1. Apple
2. Banana
3. Pear
4. vegetable

注意：有序列表不支持二级列表

## 引用

使用 `>`

```markdown
> 最外层
> > 第一层嵌套
> > > 第二层嵌套
```

> 最外层
> > 第一层嵌套
> > > 第二层嵌套

## 代码

### 行间代码

使用 \` \`

```markdown

`print("Hi There!")`

```

### 代码块

使用 \```  ``` 包裹代码，可以注明语言

``````markdown

```Python
print("hello")

```

``````

## 链接

`[Davinci的红茶馆]("https://davincievans.top")`

演示：[Davinci的红茶馆]("https://davincievans.top")

## 图片

```markdown
![alt 属性文本](图片地址)

![alt 属性文本](图片地址 "可选标题")
```

示例：`![hello](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/manifest/gallary/75778903_p0.jpg)`
![hello](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/manifest/gallary/75778903_p0.jpg)

## 表格

```markdown
|  表头   | 表头  |
|  ----  | ----  |
| 单元格  | 单元格 |
| 单元格  | 单元格 |
```

演示：
|  Fruits | Prize  |
|  ----  | ----  |
| Apple | $10 |
| Banana | $15 |

## HTML

markdown支持直接使用html来书写