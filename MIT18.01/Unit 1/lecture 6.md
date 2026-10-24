# 重点
- [2. 对数求导法（Logarithmic Differentiation）](#2.%20对数求导法（Logarithmic%20Differentiation）)
- 


# MIT 18.01SC Session 16–20 复习笔记
## 指数函数与对数函数（Exponential & Log Functions，含双曲函数）

> [!abstract] 单元概览
> - **Session 16**：从导数定义出发研究 $a^x$，引出待定量 $M(a)=\lim_{\Delta x\to0}\frac{a^{\Delta x}-1}{\Delta x}$。
> - **Session 17**：用 $M(e)=1$ 反**定义**数 $e$，得到 $\frac{d}{dx}e^x=e^x$；再用隐函数求导得到 $\frac{d}{dx}\ln x=\frac1x$，从而揭开 $M(a)=\ln a$。
> - **Session 18**：两种方法求 $\frac{d}{dx}a^x=(\ln a)a^x$，并引入**对数求导法（logarithmic differentiation）**处理 $x^x$ 这类"底和指数都动"的函数。
> - **Session 19**：用导数定义证明经典极限 $\lim_{n\to\infty}\left(1+\frac1n\right)^n=e$。
> - **Session 20**：双曲正弦/余弦（$\sinh,\cosh$）的定义、导数与恒等式。
>
> 主线一句话：**整个单元的核心是"先承认 $e^x$ 的导数是自己，再反推出 $M(a)$ 到底是什么"**。

---

## Session 16：$a^x$ 的导数与 $M(a)$

### 1. 指数运算律回顾

对 $a>0$：
$$a^{x_1+x_2}=a^{x_1}a^{x_2},\qquad (a^{x_1})^{x_2}=a^{x_1x_2},\qquad a^0=1,\ a^1=a$$
有理数指数 $a^{p/q}=\sqrt[q]{a^p}$；无理数指数通过"补全空隙"（连续性）定义。

### 2. 从导数定义出发

按定义：
$$\frac{d}{dx}a^x=\lim_{\Delta x\to0}\frac{a^{x+\Delta x}-a^x}{\Delta x}$$
用 $a^{x+\Delta x}=a^x a^{\Delta x}$ 把 $a^x$ 提出来（取极限时它是常数）：
$$\frac{d}{dx}a^x=a^x\cdot\underbrace{\lim_{\Delta x\to0}\frac{a^{\Delta x}-1}{\Delta x}}_{M(a)}$$
> [!important] 关键式子
> $$\frac{d}{dx}a^x=M(a)\,a^x$$
> 其中 $M(a)=\lim_{\Delta x\to0}\frac{a^{\Delta x}-1}{\Delta x}$。

### 补充
- [补充 3](#补充%203)


### 3. $M(a)$ 的几何意义

把 $x=0$ 代入导数定义：
$$\left.\frac{d}{dx}a^x\right|_{x=0}=M(a)\,a^0=M(a)$$
所以 **$M(a)$ 就是曲线 $y=a^x$ 在 $x=0$ 处切线的斜率**。

> ![](./图片/lecture%206-m(a).png)
> 图：$y=a^x$ 在 $x=0$ 处的切线斜率为 $M(a)$。只要知道 $x=0$ 处的斜率，整条曲线上任意点的斜率都被 $M(a)a^x$ 锁定。

> [!note] 与 $\sin x$ 的类比
> 求 $\frac{d}{dx}\sin x$ 时，我们也是先算出 $x=0$ 处的斜率 $\lim_{x\to0}\frac{\sin x}{x}=1$，再推导出全局公式。$a^x$ 的结构更简单（$a^{x+\Delta x}=a^x a^{\Delta x}$），但 $\lim_{\Delta x\to0}\frac{a^{\Delta x}-1}{\Delta x}$ 这一步却卡住了——我们暂时算不出它。
> 
> 链接：[1. 关键极限一：$\displaystyle\lim_{x\to 0}\frac{\sin x}{x}=1$](lecture%203.md#1.%20关键极限一：$%20displaystyle%20lim_{x%20to%200}%20frac{%20sin%20x}{x}=1$)

---

## Session 17：数 $e$、自然对数与 $M(a)=\ln a$

### 1. 反其道而行：用 $M(e)=1$ 定义 $e$

既然算不出 $M(a)$，干脆**挑一个让 $M(a)=1$ 的底**，记作 $e$：
$$M(e)=1\quad\Longleftrightarrow\quad \lim_{h\to0}\frac{e^h-1}{h}=1\quad\Longleftrightarrow\quad \left.\frac{d}{dx}e^x\right|_{x=0}=1$$
于是立刻得到本单元最该背的公式：
> [!important] 核心公式（必背）
> $$\frac{d}{dx}e^x=e^x$$
> 且 $y=e^x$ 在 $x=0$ 处切线斜率恰好为 $1$。

### 2. $e$ 为什么存在？

- $a=1$ 时 $a^x\equiv1$，斜率为 $0$，即 $M(1)=0<1$。
- 对 $y=2^x$：连接 $(0,1)$ 与 $(1,2)$ 的割线斜率为 $1$，而切线更平缓，故 $M(2)<1$。
- 对 $y=4^x$：连接 $(-\tfrac12,\tfrac12)$ 与 $(0,1)$ 的割线斜率为 $1$，而切线更陡，故 $M(4)>1$。

> ![](./图片/lecture%206-M2.png)
> 图：$y=2^x$ 在 $x=0$ 处切线斜率 $M(2)$ 小于连接 $(0,1)\to(1,2)$ 的割线斜率 $1$。

> ![](./图片/lecture%206-M4.png)
> 图：$y=4^x$ 在 $x=0$ 处切线斜率 $M(4)$ 大于连接 $(-\tfrac12,\tfrac12)\to(0,1)$ 的割线斜率 $1$。

假设 $M(a)$ 连续，则必有某个 $a\in(2,4)$ 使 $M(a)=1$——这个数就是 $e\approx2.71828$。

### 3. 自然对数 $\ln x$ 及其导数

$\ln x$ 定义为 $e^x$ 的反函数：
$$y=e^x\iff \ln y=x\qquad\text{即}\qquad e^{\ln x}=x$$
基本性质：$\ln(x_1x_2)=\ln x_1+\ln x_2$，$\ln1=0$，$\ln e=1$。

求 $\frac{d}{dx}\ln x$：设 $w=\ln x$，则 $e^w=x$，两边对 $x$ 隐函数求导：
$$e^w\frac{dw}{dx}=1\quad\Longrightarrow\quad \frac{dw}{dx}=\frac1{e^w}=\frac1x$$
> [!important] 核心公式（必背）
> $$\frac{d}{dx}\ln x=\frac1x$$

> [!note] 几何对应
> $y=\ln x$ 的图像是 $y=e^x$ 关于 $y=x$ 的镜像。$e^x$ 在 $(0,1)$ 处斜率为 $1$，故 $\ln x$ 在 $(1,0)$ 处斜率也为 $1$（反函数导数互为倒数）。定义域为 $x>0$。

### 4. 揭开 $M(a)$ 的真面目

把 $a$ 写成 $e^{\ln a}$，则
$$a^x=(e^{\ln a})^x=e^{x\ln a}$$
由链式法则（$\ln a$ 是常数）：
$$\frac{d}{dx}e^{x\ln a}=(\ln a)\,e^{x\ln a}=(\ln a)\,a^x$$
对比 $\frac{d}{dx}a^x=M(a)a^x$，立刻得到：
> [!important] 结论
> $$M(a)=\ln a,\qquad \boxed{\frac{d}{dx}a^x=(\ln a)\,a^x}$$

### 5. 为什么"自然"对数最自然？

经济学家关心的是**相对变化率** $\frac{p'}{p}$，而不是绝对涨跌：
$$\frac{p'}{p}=(\ln p)'$$
换底为 $\log_{10}$ 会多一个常数因子 $\ln10$：$(\log_{10}p)'=\frac{p'}{p\ln10}$。凡是涉及比值、百分比、相对增长率的问题，$\ln$ 都会自动出现——它不是人为主观选的底，而是数学上最简洁的选择。

> 这一部分在 lecture 7 的视频里

### 补充
- [[#补充1]]


---

## Session 18：其他指数函数的导数与对数求导法

### 1. 常见例子

$$\frac{d}{dx}2^x=(\ln2)\,2^x,\qquad \frac{d}{dx}10^x=(\ln10)\,10^x$$
即使从 $2$ 或 $10$ 出发，$\ln$ 也会不请自来。

### 2. 对数求导法（Logarithmic Differentiation）

> [!tip] 核心恒等式
> 对任意可导函数 $u(x)>0$：
> $$(\ln u)'=\frac{u'}{u}\qquad\Longleftrightarrow\qquad u'=u\,(\ln u)'$$
> 适用场景：直接求导困难，但取 $\ln$ 后变成乘积/商，反而好求。

用它重推 $\frac{d}{dx}a^x$：设 $u=a^x$，则 $\ln u=x\ln a$，两边求导：
$$\frac{u'}u=\ln a\quad\Longrightarrow\quad u'=(\ln a)a^x$$
与换成底 $e$ 的方法殊途同归。

### 3. 经典例子：$x^x$ 的导数

$x^x$ 的底和指数**都在变**，既不能用幂法则（指数不是常数），也不能用指数法则（底不是常数）。取对数：
$$\ln(x^x)=x\ln x$$
两边对 $x$ 求导（右边用乘积法则）：
$$\frac{v'}v=\ln x+x\cdot\frac1x=1+\ln x$$
于是
> [!important]
> $$\frac{d}{dx}x^x=x^x(1+\ln x)$$

> [!warning] 易错点
> - 不要把 $x^x$ 误套幂法则得到 $x\cdot x^{x-1}=x^x$，也不要误套指数法则得到 $(\ln x)x^x$——两者都错。
> - $x^x$ 的定义域是 $x>0$（否则取 $\ln$ 无意义）。

## 补充
- [补充 2](#补充%202)
 

---

## Session 19：涉及 $e$ 的一个有趣极限

证明：
$$\lim_{n\to\infty}\left(1+\frac1n\right)^n=e$$

**思路**：遇到"动指数"，先取 $\ln$ 把指数拉下来。

设 $L=\lim_{n\to\infty}\ln\left[\left(1+\frac1n\right)^n\right]$，则
$$L=\lim_{n\to\infty}n\ln\left(1+\frac1n\right)$$
令 $\Delta x=\frac1n$（$n\to\infty$ 时 $\Delta x\to0$），则 $n=\frac1{\Delta x}$：
$$L=\lim_{\Delta x\to0}\frac{\ln(1+\Delta x)}{\Delta x}$$
巧妙地减去 $\ln1=0$，凑成导数定义：
$$L=\lim_{\Delta x\to0}\frac{\ln(1+\Delta x)-\ln1}{\Delta x}=\left.\frac{d}{dx}\ln x\right|_{x=1}=\frac1x\bigg|_{x=1}=1$$
再指数还原：
$$\lim_{n\to\infty}\left(1+\frac1n\right)^n=e^L=e^1=e$$

> [!note] 数值感受
> $\left(1+\frac1{10000}\right)^{10000}\approx2.7182$，已接近 $e$。这个极限同时也是 $e$ 的一个**数值计算公式**。

> [!tip] 技巧
> 当极限形如 $\frac{\ln(1+\Delta x)-\ln1}{\Delta x}$ 时，认出它就是 $\ln x$ 在 $x=1$ 处的导数定义——"加一项减一项凑导数定义"是微积分里的常用手法。

---

## Session 20：双曲函数（Hyperbolic Functions）

### 1. 定义

> [!important] 双曲正弦与双曲余弦
> $$\sinh x=\frac{e^x-e^{-x}}{2}\qquad\text{（读作"sinh"）}$$
> $$\cosh x=\frac{e^x+e^{-x}}{2}\qquad\text{（读作"cosh"）}$$

### 2. 导数

直接对定义式求导（注意 $\frac{d}{dx}e^{-x}=-e^{-x}$）：
$$\frac{d}{dx}\sinh x=\frac{e^x-(-e^{-x})}{2}=\cosh x$$
$$\frac{d}{dx}\cosh x=\frac{e^x+(-e^{-x})}{2}=\sinh x$$

> [!warning] 与三角函数的关键区别
> $$\frac{d}{dx}\cos x=-\sin x\quad\text{（带负号）}\qquad\text{但}\qquad\frac{d}{dx}\cosh x=+\sinh x\quad\text{（不带负号）}$$

### 3. 双曲恒等式

展开验证：
$$\cosh^2x-\sinh^2x=\frac{(e^x+e^{-x})^2-(e^x-e^{-x})^2}{4}=\frac{4}{4}=1$$

> [!note] 为什么叫"双曲"？
> 若令 $u=\cosh x,\ v=\sinh x$，则 $u^2-v^2=1$——这是**双曲线（hyperbola）**方程。
> 而三角函数 $\cos x,\sin x$ 满足 $u^2+v^2=1$——这是**单位圆（circle）**方程。一圆一双，形成对偶。

### 课后作业补充：双曲三角公式

**目标**：将 $(\boldsymbol{\sinh(x+y)}$)、$(\boldsymbol{\cosh(x+y)}$) 展开为$\sinh x,\cosh x,\sinh y,\cosh y$ 的表达式。

#### 预备定义
双曲正弦与双曲余弦的指数形式：
$$
\sinh u = \frac{e^u - e^{-u}}{2}, \quad \cosh u = \frac{e^u + e^{-u}}{2}
$$

---

#### 一、$\boldsymbol{\boldsymbol{\sinh(x+y)}}$ 的展开
从指数定义出发：
$$
\begin{align*}
\$\boldsymbol{\sinh(x+y)}$ &= \frac{e^{x+y} - e^{-(x+y)}}{2} \\
&= \frac{1}{2}\left(e^{x+y} - e^{-x-y}\right)
\end{align*}
$$

对分子配凑拆分，构造双曲函数的乘积形式：
$$
\begin{align*}
\boldsymbol{\sinh(x+y)} &= \frac{1}{4}\left(2e^{x+y} - 2e^{-x-y}\right) \\
&= \frac{1}{4}\left[(e^x + e^{-x})(e^y - e^{-y}) + (e^x - e^{-x})(e^y + e^{-y})\right] \\
&= \frac{e^x + e^{-x}}{2} \cdot \frac{e^y - e^{-y}}{2} + \frac{e^x - e^{-x}}{2} \cdot \frac{e^y + e^{-y}}{2}
\end{align*}
$$

代入定义化简，得到和角公式：
$$
\boldsymbol{\boldsymbol{\sinh(x+y)} = \cosh x \sinh y + \sinh x \cosh y}
$$

> 对比三角函数：$\sin(x+y) = \sin x \cos y + \cos x \sin y$，形式完全一致。

---

#### 二、$\boldsymbol{\boldsymbol{\cosh(x+y)}}$ 的展开
同样从指数定义出发：
$$
\begin{align*}
\boldsymbol{\cosh(x+y)} &= \frac{e^{x+y} + e^{-(x+y)}}{2} \\
&= \frac{1}{2}\left(e^{x+y} + e^{-x-y}\right)
\end{align*}
$$

对分子配凑拆分：
$$
\begin{align*}
\boldsymbol{\cosh(x+y)} &= \frac{1}{4}\left(2e^{x+y} + 2e^{-x-y}\right) \\
&= \frac{1}{4}\left[(e^x + e^{-x})(e^y + e^{-y}) + (e^x - e^{-x})(e^y - e^{-y})\right] \\
&= \frac{e^x + e^{-x}}{2} \cdot \frac{e^y + e^{-y}}{2} + \frac{e^x - e^{-x}}{2} \cdot \frac{e^y - e^{-y}}{2}
\end{align*}
$$

代入定义化简，得到和角公式：
$$
\boldsymbol{\boldsymbol{\cosh(x+y)} = \cosh x \cosh y + \sinh x \sinh y}
$$

> 对比三角函数：$\cos(x+y) = \cos x \cos y - \sin x \sin y$，区别在于第二项符号为**正号**。


### 补充
- [补充 4](#补充%204)

---

## 总结

> [!important] 必背公式
> $$
> \begin{aligned}
> &\frac{d}{dx}e^x = e^x \\
> &\frac{d}{dx}\ln x = \frac1x \\
> &\frac{d}{dx}a^x = (\ln a)\,a^x \\
> &\frac{d}{dx}x^x = x^x(1+\ln x) \\
> &\frac{d}{dx}\sinh x = \cosh x,\qquad \frac{d}{dx}\cosh x = \sinh x \\
> &\cosh^2x-\sinh^2x = 1 \\
> &\lim_{n\to\infty}\left(1+\frac1n\right)^n = e
> \end{aligned}
> $$

> [!danger] 三大陷阱
> 1. 求 $x^x$ 时**乱套幂法则或指数法则**——必须先用对数求导法。
> 2. 把 $\cosh$ 的导数误记成 $-\sinh$（那是 $\cos$ 的导数）。
> 3. 看到 $\lim_{n\to\infty}(1+1/n)^n$ 时，误以为 $(1+1/n)\to1$ 所以极限是 $1$——**指数 $n$ 同时在发散**，不能拆开看。

---

## 思维导图
![717](./图片/lecture%206-mindmap.svg)

## 补充1
 > e的之前的数列极限定义和这总定义等价吗？
 
两种定义完全等价，可以互相推导

#### 1. 从极限定义 → 导数定义
已知 $e = \lim_{t\to0}(1+t)^{\frac{1}{t}}$，证明 $\lim_{h\to0}\frac{e^h - 1}{h} = 1$：

令 $t = e^h - 1$，则 $h = \ln(1+t)$；当 $h\to0$ 时，$t\to0$。代入极限得：
$$
\lim_{h\to0}\frac{e^h - 1}{h} = \lim_{t\to0}\frac{t}{\ln(1+t)} = \lim_{t\to0}\frac{1}{\frac{1}{t}\ln(1+t)} = \lim_{t\to0}\frac{1}{\ln(1+t)^{\frac{1}{t}}}
$$

由e的极限定义，$\lim_{t\to0}(1+t)^{\frac{1}{t}} = e$；结合对数函数的连续性：
$$
\lim_{t\to0}\ln(1+t)^{\frac{1}{t}} = \ln\left(\lim_{t\to0}(1+t)^{\frac{1}{t}}\right) = \ln e = 1
$$

因此原式 $= \frac{1}{1} = 1$，即导数型定义成立。

#### 2. 从导数定义 → 极限定义
已知 $\lim_{h\to0}\frac{e^h - 1}{h} = 1$，证明 $e = \lim_{n\to\infty}\left(1+\frac{1}{n}\right)^n$：

由导数定义可先推导出自然对数 $\ln x$（$e^x$ 的反函数）的导数：
设 $y=\ln x$，则 $x=e^y$，由反函数求导法则得 $(\ln x)' = \frac{1}{x}$。
在 $(x=1$ ) 处用导数定义展开：
$$
(\ln x)'\bigg|_{x=1} = \lim_{\Delta x\to0}\frac{\ln(1+\Delta x)}{\Delta x} = 1
$$

令 $\Delta x = \frac{1}{n}$（$n\to\infty$ 时 $\Delta x\to0$），代入得：
$$
\lim_{n\to\infty} n\cdot\ln\left(1+\frac{1}{n}\right) = 1 \implies \lim_{n\to\infty}\ln\left(1+\frac{1}{n}\right)^n = 1
$$

两边同时取 $e$ 的指数（指数函数连续）：
$$
e^{\lim_{n\to\infty}\ln\left(1+\frac{1}{n}\right)^n} = e^1 \implies \lim_{n\to\infty}\left(1+\frac{1}{n}\right)^n = e
$$

即极限型定义成立。

### 补充说明
除了以上两种，$e$ 还有级数定义 $e = \sum_{n=0}^{\infty}\frac{1}{n!}$、积分定义（$\ln x = \int_1^x \frac{1}{t}dt$ 的反函数在1处的值）等，所有这些定义都是**互相等价**的。

教材选择哪种定义，只是取决于教学的切入顺序：
- 极限定义更偏向“分析基础”，先讲极限再定义e；
- 图中的导数定义更偏向“微积分应用”，直接突出 $e^x$ 求导等于自身的核心性质，是微积分里最实用的视角。

# 补充 2

 > 除了 $x^x$，还有哪些用对数求导法的经典例子？
 
### 一、多个函数连乘/连除/带根式型
这类题直接用乘积/商的求导法则会非常繁琐，取对数后变成加减法，求导效率极高。

#### 例1：复杂分式连乘
求 $\displaystyle y = \frac{x(x+1)(x-2)}{(x+3)(x-4)}$ 的导数
1.  两边取自然对数（定义域内保证真数为正，严格写法可加绝对值）：
    $$\ln|y| = \ln|x| + \ln|x+1| + \ln|x-2| - \ln|x+3| - \ln|x-4|$$
2.  两边对 $x$ 隐函数求导：
    $$\frac{y'}{y} = \frac{1}{x} + \frac{1}{x+1} + \frac{1}{x-2} - \frac{1}{x+3} - \frac{1}{x-4}$$
3.  两边乘 $y$ 得到最终导数：
    $$y' = \frac{x(x+1)(x-2)}{(x+3)(x-4)} \cdot \left( \frac{1}{x} + \frac{1}{x+1} + \frac{1}{x-2} - \frac{1}{x+3} - \frac{1}{x-4} \right)$$

#### 例2：带根号的分式（最经典考试题型）
求 $\displaystyle y = \sqrt{\frac{(x-1)(x-2)}{(x-3)(x-4)}}$ 的导数
1.  取对数，把根号转化为 $\frac{1}{2}$ 倍：
    $$\ln y = \frac{1}{2}\left[ \ln(x-1) + \ln(x-2) - \ln(x-3) - \ln(x-4) \right]$$
2.  两边求导：
    $$\frac{y'}{y} = \frac{1}{2}\left( \frac{1}{x-1} + \frac{1}{x-2} - \frac{1}{x-3} - \frac{1}{x-4} \right)$$
3.  整理结果：
    $$y' = \frac{1}{2}\sqrt{\frac{(x-1)(x-2)}{(x-3)(x-4)}} \cdot \left( \frac{1}{x-1} + \frac{1}{x-2} - \frac{1}{x-3} - \frac{1}{x-4} \right)$$

---

### 二、一般幂指函数 $u(x)^{v(x)}$ 型
底和指数都是关于 $x$ 的函数，既不能套幂函数法则，也不能套指数函数法则，是对数求导法的核心应用场景。

#### 例3：$y = (\sin x)^{\cos x}$（$\sin x>0$ 的区间）
1.  取对数：
    $$\ln y = \cos x \cdot \ln(\sin x)$$
2.  右边用乘积法则求导：
    $$\frac{y'}{y} = -\sin x \cdot \ln(\sin x) + \cos x \cdot \frac{\cos x}{\sin x}$$
    $$\frac{y'}{y} = \cos x \cdot \cot x - \sin x \cdot \ln(\sin x)$$
3.  最终结果：
    $$y' = (\sin x)^{\cos x} \cdot \left( \cos x \cot x - \sin x \cdot \ln(\sin x) \right)$$

#### 例4：$y = x^{\ln x}$
1.  取对数：
    $$\ln y = (\ln x)^2$$
2.  复合函数求导：
    $$\frac{y'}{y} = 2\ln x \cdot \frac{1}{x}$$
3.  整理：
    $$y' = \frac{2\ln x}{x} \cdot x^{\ln x} = 2 \cdot x^{\ln x -1} \cdot \ln x$$

---

### 三、多类型函数混合连乘型
不同类型函数（幂函数、三角函数、指数函数）相乘，对数求导法比多次乘积法则更简洁。

#### 例5：$y = x \cdot \sin x \cdot 2^x$
1.  取对数：
    $$\ln y = \ln x + \ln(\sin x) + x\ln2$$
2.  逐项求导：
    $$\frac{y'}{y} = \frac{1}{x} + \cot x + \ln2$$
3.  结果：
    $$y' = x \cdot \sin x \cdot 2^x \cdot \left( \frac{1}{x} + \cot x + \ln2 \right)$$

---

### 补充要点
1.  **定义域问题**：严格来说取对数时应写 $\ln|y|$，保证真数为正；求导后绝对值会自动消去，最终结果和不加绝对值一致。
2.  **等价方法**：对数求导法和「先改写为指数形式 $y = e^{\ln y}$ 再求导」本质完全等价，比如 $x^x = e^{x\ln x}$ 求导结果和图中完全一致。
3.  **易错提醒**：幂指函数绝对不能直接套幂函数（$x^n$）或指数函数（$a^x$）的求导公式，两种错误套法都和正确结果差很远。


## 补充 3
> $\lim_{x \to 0} \frac{a^x - 1}{x}$ 直接计算的方法

$$
\lim_{x \to 0} \frac{a^x - 1}{x}
= \lim_{x \to 0} \frac{e^{x\ln a} - 1}{x}
= \lim_{x \to 0} \frac{x\ln a}{x}
= \ln a
$$


## 补充 4
> 如果说三件函数里的自变量x表示和x正半轴的夹角，那么双曲三角的自变量有什么含义？

自变量 a 是双曲扇形的面积的两倍（类似于三角函数中 $\theta$ 是扇形面积的两倍）
![](./图片/lecture%206-1791819612931.jpg)

## 有意思的（课后视频）
$$
-\ln{\cos{x}}=\tan{x}
$$
