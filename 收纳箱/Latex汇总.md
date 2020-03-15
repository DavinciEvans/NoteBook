# Latex 常用公式汇总

## 常规

$$
x_a^b + \alpha
$$

```Latex
x_a^b+\alpha
```

$$
2\frac{1}{2}
$$

```Latex
$$
2\frac{1}{2}
$$
```

$$
\sum_{i=1}^{n} \pm \prod_2^5
$$

```Latex
$$
\sum_{i=1}^{n} \pm \prod^5
$$
```

$$
\sqrt{2} + \sqrt[3]{2}
$$

```Latex
$$
\sqrt{2} + \sqrt[3]{2}
$$
```

## 微积分

$$
\lim_{x\to0}\frac{1}{X} = \infty
$$

```Latex
$$
\lim_{x\to0}\frac{1}{X} = \infty
$$
```

$$
\int_{a}^{b}g(x)\mathrm{d}x+\oint_{a}^{b}g(x)\mathrm{d}x+\iint_{a}^{b}g(x)\mathrm{d}x + \oiint_{a}^{b}g(x)\mathrm{d}x + \iiint_{a}^{b}g(x)\mathrm{d}x
$$

```Latex
$$
\int_{a}^{b}g(x)\mathrm{d}x + \oint_{a}^{b}g(x)dx + \iint_{a}^{b}g(x)dx + \oiint_{a}^{b}g(x)dx + \iiint_{a}^{b}g(x)dx
$$
```

注：\mathrm{}的含义为去掉该处的数学渲染，在标准公式中d不斜体。

$$
\frac{\partial}{\partial x}
$$

```Latex
$$
\frac{\partial}{\partial x}
$$
```

## 方程组与不等式组

$$
\begin{cases}
 & y=x^2, x<0 \\
 & y=x, 0\leqslant{x}<1 \\
 & y=\frac{1}{x}, x\geqslant1
\end{cases}
$$

```Latex
$$
\begin{cases}
 & y=x^2, x<0 \\
 & y=x, 0\leqslant{x}<1 \\
 & y=\frac{1}{x}, x\geqslant1
\end{cases}
$$
```

$$
y = \frac{1}{x}, x \in [-1, 1]且x \neq 0
$$

```Latex
$$
y = \frac{1}{x}, x \in [-1, 1]且x \neq 0
$$
```

## 矩阵

$$
\begin{matrix}
2 &  3& 5\\
2 &  5& 8\\
2 &  0& 0
\end{matrix}
+
\begin{pmatrix}
2 &  3& 5\\
2 &  5& 8\\
2 &  0& 0
\end{pmatrix}

$$

```Latex
$$
\begin{matrix}
2 &  3& 5\\
2 &  5& 8\\
2 &  0& 0
\end{matrix}
+
\begin{pmatrix}
2 &  3& 5\\
2 &  5& 8\\
2 &  0& 0
\end{pmatrix}

$$
```
