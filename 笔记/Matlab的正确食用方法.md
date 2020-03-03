# Matlab的正确食用方法

大多数计算、绘图可以直接在命令行窗口进行执行。

**clear**：清空赋值

## 数学运算

- +、-、*、/

- 相同矩阵的同位相乘：.*

- 幂：^

**%···%**：注释

分号代表后面还有指令，若没有分号结尾则在命令行直接计算。

## M文件

以 `function 因变量名=函数名(自变量)` 作为第一行

举个栗子：

```Matlab
function y = new(x):

y = (x - 1) + (x + 2) ^ 2
```

保存为 `new.m`

若想运行则在命令行输入

```matlab
>>> x=4
>>> new(4)
```

则可以得到new(4)

## 矩阵、向量

- **向量**：x = `[1 2 3 4 5 6]` 或 `[1, ,2, 3, 4, 5, 6]`

- **矩阵**：x = `[1 2 3;4 5 6;7 8 9]`

- **列向量**：x = `[1;2;3;4;5;6]`

**行向量与列向量互换**：`y = x'`

**特殊矩阵**：

- `A=eye(m,n)`：m * n 的单位矩阵

```Matlab
>>>A=eye(2,4)
A=
1 0 0 0
0 1 0 0
```

- `B=zeros(m,n)`：m * n 的零矩阵

```Matlab
>>>B=zeros(2,4)
B=
0 0 0 0
0 0 0 0
```

### 定义复杂数组

- `m:n = m,m+1,m+2...n`

- `m:k:n = m,m+k,m+2k...n`

- `x = linspace(m,n,k)`：将区间[m,n]平均分成k份，取两端

### 数组与数字之间的运算

令X = [a,b,c]，q是常数。

- X+q=$$[a+q,b+q,c+q]$$（减法同理）

- X\*q= $$[a*q,b*q,c*q]$$

- X/q=$$[\frac{a}{q},\frac{b}{q},\frac{c}{q}]$$

- X.\q=$$[\frac{q}{a},\frac{q}{b},\frac{q}{c}]$$

- X^q=$$[a^q,b^q,c^q]$$

- X.^q=$$[q^a,q^b,q^c]$$

### 数组与数组间的运算

令X=[a,b]，Y=[c,d]。

- X+Y=$$[a+c,b+d]$$

- X.\*Y=$$[a*c,b*d]$$

- X./Y=$$[\frac{a}{c},\frac{b}{d}]$$

- X.\Y=$$[\frac{c}{a},\frac{d}{b}]$$

### 分割矩阵

和Python类似，使用`:`进行分割

```Matlab
A=
1 0 0 0 0
0 1 0 0 0
0 0 1 0 0

>>>A(1:2,2:3)
%1~2行,2~3列

ars=

0 0
1 0

>>>A(1:2,:)
%1~2行
ars=

1 0 0 0 0
0 1 0 0 0
```

### 合并矩阵

矩阵要能够合并，否则会报错

```Matlab
A=
1 2
3 4

B=
5 6
7 8

>>>[A B]
%A左B右

ars=

1 2 5 6
3 4 7 8

>>>[A;B]
%A上B下

ars=
1 2
3 4
5 6
7 8
```

### 矩阵运算

**同行矩阵相加和相乘**：

```Matlab
A =

     1     2
     3     4

>> B=A

B =

     1     2
     3     4

>> A+B

ans =

     2     4
     6     8

>> A*B

ans =

     7    10
    15    22

```

**求方阵行列式**：`det(A)`

```Matlab
>> det(A)

ans =

    -2
```

**求逆矩阵**：`inv(A)`

```Matlab
>> inv(A)

ans =

   -2.0000    1.0000
    1.5000   -0.5000
```

**除法**：看除号往哪边斜

```Matlab
>> A/B
%左除：即为B*X=A

ans =

     1     0
     0     1

>> A\B
%右除，即为A*X=B

ans =

    1.0000         0
    0.0000    1.0000
```

## 控制流结构

### 循环

- for-end

```Matlab
>>for i=1:50;
%传入一个数组
s=s+i;
end

>>s

s=

1275

>>for n=1:5;
x(n)=sin(pi/n);
end

>>x(2)

ans=

1

>>x

0.0000 1.0000 0.8660 0.7071 0.5878
```

- while-end

```Matlab
while m<5;
t=t+1;
m=m*(1+0.03);
end
```

### 选择

```Matlab
if x<0
     f=2*x+sin(x)
else x>=0
     f=exp(x)-1
end
```

--------

```Matlab
if x<-1
     f=-1
elseif x>=-1&x<=1
     f=0
elseif x>1
     f=1
end
```

## 作图

### 普通作图

`plot(x,y'S')`

x，y 是点的集合，S 是线形。

```Matlab
>> x=[0:0.01:2*pi];
>> y=sin(x);
>> plot(x,y)
```

![sin](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/gallery/QQ截图20200303112653.png)

```Matlab
>> y2=sin(x+1);
>> plot(x,y,'S',x,y2,'--')
```

![两个sin图像](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/gallery/QQ截图20200303113007.png)

**绘制自定义函数**：`fpot` 可以绘制使用m文件自定义的函数。

举个栗子：`fplot('myfun',[0,2])

**图像注释**：x 轴上添加：xlabel('注释')，y、z 同理。在上端添加用title('注释')

**显示网格**：`grid on` 指令

**分割图像窗口**：`subplot(m,n,k)`

分割成 m*n 块，激活第k块

使用subplot(1,1,1)合并

### 绘制隐函数或参数方程

`plot` 不能绘制隐函数、参数方程

使用 `ezplot` 绘制。

- `explot('f(x)', [a,b])`

绘制 $$y=f(x)$$ 在 $$[a,b]$$ 上的图像。

- `explot('f(x,y)',[a,b,c,d])`

绘制隐函数 $$f(x,y)=0$$ 在 $$x\in[a,b]$$ 且 $$y\in[c,d]$$上的图像。

- `explot('x(t)','y(t)',[a,b])`

绘制(x(t),y(t))在$$t\in[a,b]$$上的图像。

### 极坐标绘图

极坐标方程一般为 $$r=f(\theta)$$

`polar(theta, r, 'S')`

### 三维绘图

**三维曲线**的一般方程为：$$x=f(t),y=g(t),z=t$$

`plot3(x,y,z,'S')`

```Matlab
>> x=-3:0.1:3;
>> y=0:0.01:2*pi;
>> y=0:0.1:2*pi;
>> [x,y]=meshgrid(x,y);
>> z=x.*sin(y)+4*x.*cos(y);
>> plot3(x,y,z);
```

![曲线](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/gallery/QQ截图20200303190926.png)

其中 `meshgrid` 的含义为将 x,y 所在的区域中所有的点形成一个矩阵，并重新赋值给 x,y。

该图为不同的 x 取值时的各个曲线。

**三维曲面**使用 `surf(x,y,z)`

![平面](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/gallery/QQ截图20200303204449.png)

使用 `shading flat` 指令让图像更平滑。

![光滑平面](https://cdn.jsdelivr.net/gh/DavinciEvans/Imgs-bed@master/gallery/QQ截图20200303204819.png)

### 散点图

使用 `plot(x,y,'k')` 或者 `scatter(x,y,'k')`

`plot` 的图为折线图，`scatter` 的图为散点图。
