# 重点
其实大部分内容高中都学过。
- [9. 高阶导数的记号（Notations）](#9.%20高阶导数的记号（Notations）)

# MIT 18.01 Session 9–12 复习笔记：求导法则体系（Rules for Differentiation）

> [!info] 整体脉络
> - **Session 9–10**：在幂函数、$\sin x$、$\cos x$ 等**具体求导公式（specific rules）**与常数倍、和法则之上，解决"函数相乘、相除怎么求导"——**乘法法则（Product Rule）**、**除法法则（Quotient Rule）**（含基于导数定义的证明），并通过**倒数（reciprocal）**例题把幂法则推广到负指数。
> - **Session 11**：**链式法则（Chain Rule）**，解决**复合函数（composition of functions）**求导。
> - **Session 12**：**高阶导数（Higher Derivatives）**、多种导数记号，以及 $D^n x^n=n!$ 经典例题。

---

## 1. 已学法则回顾

| 法则（英文） | 公式 |
| --- | --- |
| 幂法则（Power Rule） | $\dfrac{d}{dx}x^n = nx^{n-1}$ |
| 常数倍法则（Constant Multiple Rule） | $(cu)' = c\cdot u'$ |
| 和法则（Sum Rule） | $(u+v)' = u' + v'$ |

---

## 2. 乘法法则（Product Rule）

### 2.1 公式

$$
(uv)' = u'v + uv'
$$

> [!tip] 记忆方式：一次只变一个函数（change one function at a time）
> 第一项只对 $u$ 求导（$v$ 保持不变），第二项只对 $v$ 求导（$u$ 保持不变），再相加。这是处理"多个函数组合在一起"求导的通用程序（general procedure），后续所有法则都遵循同一思想。

> [!warning] 最常见错误
> 乘积的导数**不是**导数的乘积：$(uv)' \neq u'v'$，而是两项之和。

### 2.2 例题：$\dfrac{d}{dx}\,x^n\sin x$

令 $u=x^n$，$v=\sin x$，则 $u'=nx^{n-1}$（幂法则），$v'=\cos x$，代入乘法法则：

$$
\frac{d}{dx}\,x^n\sin x = nx^{n-1}\sin x + x^n\cos x
$$

### 2.3 推广到三个函数相乘

反复套用乘法法则：

$$
(uvw)' = u'vw + uv'w + uvw'
$$

规律：$n$ 个函数相乘，导数就是 $n$ 项之和，**每一项中恰好有一个函数被求导**，其余保持不变。

### 2.4 证明（从导数定义出发）

**第一步：写出差商（difference quotient）定义**

$$
(uv)' = \lim_{\Delta x \to 0}\frac{u(x+\Delta x)v(x+\Delta x)-u(x)v(x)}{\Delta x}
$$

**第二步："加零"技巧（add zero）**——注意到恒等式

$$
u(x+\Delta x)v(x) - u(x+\Delta x)v(x) = 0
$$

把它加进分子（加零不改变表达式的值），再重新分组：==（应该说是为了把 $u$ 的变化量配成一组，而引入了无关的项，再通过配凑并 合并同类项）==

$$
(uv)' = \lim_{\Delta x \to 0}\left[\frac{u(x+\Delta x)-u(x)}{\Delta x}\,v(x) + u(x+\Delta x)\,\frac{v(x+\Delta x)-v(x)}{\Delta x}\right]
$$

**第三步：取极限。** 两个差商分别趋于 $u'(x)$、$v'(x)$；又因为**可微必连续（differentiable $\Rightarrow$ continuous）**，所以

$$
\lim_{\Delta x \to 0}u(x+\Delta x) = u(x)
$$

且"和的极限等于极限的和"，最终得到

$$
(uv)' = u'(x)v(x) + u(x)v'(x)
$$

> [!note] 证明的核心套路
> 导数定义中分子是"整体增量"，通过**加一项再减同一项**把它拆成分别含 $u$ 增量和 $v$ 增量的两部分；连续性保证 $u(x+\Delta x)\to u(x)$。商法则的证明也是同一思路。

---

## 3. 除法法则（Quotient Rule）

### 3.1 公式

$$
\left(\frac{u}{v}\right)' = \frac{u'v - uv'}{v^2}\qquad (v \neq 0)
$$

> [!tip] 记忆要点
> 分子 $u'v-uv'$ 的结构与乘法法则一致（**先对分子 $u$ 求导**写在前面），分母是 $v^2$；中间是**减号且顺序不能反**（反了结果整体变号）。

### 3.2 证明

**第一步：写出定义。**

$$
\left(\frac{u}{v}\right)' = \lim_{\Delta x \to 0}\frac{\dfrac{u(x+\Delta x)}{v(x+\Delta x)}-\dfrac{u(x)}{v(x)}}{\Delta x}
$$

**第二步：引入增量记号** $\Delta u = u(x+\Delta x)-u(x)$，$\Delta v = v(x+\Delta x)-v(x)$，即 $u(x+\Delta x)=u+\Delta u$、$v(x+\Delta x)=v+\Delta v$。对分子中的两个分式**通分（common denominator）**：

$$
\frac{u+\Delta u}{v+\Delta v}-\frac{u}{v}
= \frac{(u+\Delta u)v-u(v+\Delta v)}{(v+\Delta v)v}
= \frac{(\Delta u)v-u(\Delta v)}{(v+\Delta v)v}
$$

**第三步：代回差商并整理。**

$$
\frac{\dfrac{u(x+\Delta x)}{v(x+\Delta x)}-\dfrac{u(x)}{v(x)}}{\Delta x}
= \frac{\left(\dfrac{\Delta u}{\Delta x}\right)v-u\left(\dfrac{\Delta v}{\Delta x}\right)}{(v+\Delta v)v}
$$

**第四步：取极限（$\Delta x \to 0$）。** $\dfrac{\Delta u}{\Delta x}\to\dfrac{du}{dx}$，$\dfrac{\Delta v}{\Delta x}\to\dfrac{dv}{dx}$；$v$ 可微故连续，$v+\Delta v\to v$，分母趋于 $v^2$，于是

$$
\left(\frac{u}{v}\right)' = \frac{v\,\dfrac{du}{dx}-u\,\dfrac{dv}{dx}}{v^2} = \frac{u'v-uv'}{v^2}
$$

---

## 4. 应用例题：倒数（Reciprocals）

令 $u=1$（常数的导数为 $0$，即 $\dfrac{du}{dx}=0$），$v$ 为任意函数（$\dfrac{dv}{dx}=v'$），代入商法则：

$$
\frac{d}{dx}\left(\frac{1}{v}\right)
= \frac{0\cdot v - 1\cdot v'}{v^2}
= -\frac{v'}{v^2}
= -v^{-2}v'
$$

这就是**倒数法则（Reciprocal Rule）**。再取 $v=x^n$，此时 $v'=nx^{n-1}$：

$$
\frac{d}{dx}\left(\frac{1}{x^n}\right)
= -(x^n)^{-2}(nx^{n-1})
= -x^{-2n}\cdot nx^{n-1}
= -nx^{-n-1}
$$

而 $\dfrac{1}{x^n}=x^{-n}$，所以

$$
\frac{d}{dx}x^{-n} = -nx^{-n-1}
$$

> [!important] 核心结论
> 这与正指数幂法则 $\dfrac{d}{dx}x^n=nx^{n-1}$ 形式完全一致——**幂法则（Power Rule）对负整数指数 $n$ 同样成立**，商法则为它提供了证明。

---

## 5. Session 9–10 法则速查表

| 法则 | 公式 | 备注 |
| --- | --- | --- |
| 幂法则 Power Rule | $(x^n)'=nx^{n-1}$ | $n$ 为正、负整数均成立 |
| 常数倍 Constant Multiple | $(cu)'=cu'$ | |
| 和法则 Sum Rule | $(u+v)'=u'+v'$ | |
| 乘法法则 Product Rule | $(uv)'=u'v+uv'$ | 一次只导一个 |
| 除法法则 Quotient Rule | $\left(\dfrac{u}{v}\right)'=\dfrac{u'v-uv'}{v^2}$ | $v\neq 0$，减号顺序 |
| 倒数法则 Reciprocal Rule | $\left(\dfrac{1}{v}\right)'=-\dfrac{v'}{v^2}$ | 商法则 $u=1$ 的特例 |

> [!summary] 两个证明的共同方法论
> 1. 回到导数定义（差商极限）；
> 2. 用代数技巧（乘积"加零"、商"通分 + $\Delta u/\Delta v$ 增量记号"）把整体增量拆成单个函数的差商；
> 3. 用"可微 $\Rightarrow$ 连续"处理 $u(x+\Delta x)\to u(x)$、$v+\Delta v\to v$；
> 4. 用极限四则运算法则收束。

---

# Session 11：链式法则（Chain Rule）

## 6. 复合函数（Composition of Functions）

**复合**（composition）的本质是**代入**（substitution）：先把 $x$ 代入 $g$，再把结果 $g(x)$ 代入 $f$，记作

$$
(f\circ g)(x) = f(g(x))
$$

数据流向（对应笔记中的"函数机器"示意图）：

$$
x \;\xrightarrow{\;g\;}\; g(x) \;\xrightarrow{\;f\;}\; f(g(x))
$$

以 $y=(\sin t)^{10}$（通常写成 $y=\sin^{10}t$）为例，**引入中间变量（intermediate variable）** 拆成两层：

- **内层函数（inside function）**：$x=\sin t$
- **外层函数（outside function）**：$y=x^{10}$

代回即可还原：把 $x=\sin t$ 代入 $y=x^{10}$ 仍得到 $y=\sin^{10}t$。

> [!tip] 方法论
> 当引入新变量能让结构变清晰时，就大胆引入中间变量——链式法则是这一做法最典型的场景。

## 7. 链式法则（Chain Rule）

### 7.1 直观推导：差商相乘

目标是求 $y$ 对原始变量 $t$ 的变化率。割线斜率（slopes of secant lines）满足

$$
\frac{\Delta y}{\Delta t} = \frac{\Delta y}{\Delta x}\cdot\frac{\Delta x}{\Delta t}
$$

相乘时中间的小增量 $\Delta x$ 恰好约掉（cancel）。令 $\Delta t\to 0$；因 $x=\sin t$ 连续，$\Delta t\to 0$ 时 $\Delta x\to 0$，于是 

$$
\lim_{\Delta t\to 0}\frac{\Delta y}{\Delta t}
= \frac{dy}{dt}
= \frac{dy}{dx}\cdot\frac{dx}{dt}
\qquad \longleftarrow \textbf{The Chain Rule!}
$$

> [!important] 链式法则（Chain Rule）
> **复合函数的导数是各层导数的乘积**：外层对中间变量求导，再乘以内层对原变量求导。
> $$\frac{d}{dx}f(g(x)) = f'(g(x))\,g'(x)$$

### 7.2 例题：$\dfrac{d}{dt}\sin^{10}t$

外层 $y=x^{10}$：$\dfrac{dy}{dx}=10x^9$；内层 $x=\sin t$：$\dfrac{dx}{dt}=\cos t$。由链式法则：

$$
\frac{d}{dt}\sin^{10}t = 10x^9\cdot\cos t
$$

> [!warning] 最后一步：换回原变量（rewrite in terms of $t$）
> 中间变量 $x$ 只是辅助，最终答案里不能留 $x$，必须代回：
> $$\frac{d}{dt}\sin^{10}t = 10(\sin t)^9\cdot\cos t = 10\sin^9 t\cdot\cos t$$

> [!note] 使用要点
> 1. 分清**谁是内层、谁是外层**；
> 2. 外层求导时**保持内层原样代入**（$f'$ 在 $g(x)$ 处取值，即 $f'(g(x))$）；
> 3. 别漏乘内层导数 $g'(x)$；
> 4. 多层复合就逐层求导相乘，最后统一换回原变量。

---

# Session 12：高阶导数（Higher Derivatives）

## 8. 定义与例子

**高阶导数（higher derivatives）就是"导数的导数"。** 若 $u=u(x)$ 可微，$u'$ 是一个新函数，对它再求导得 $(u')'=u''$（**二阶导数，second derivative**），继续下去：

$$
u \to u' \to u'' \to u'''=u^{(3)} \to u^{(4)} \to \cdots \to u^{(n)}
$$

以 $u(x)=\sin x$ 为例：

$$
u'=\cos x,\qquad u''=-\sin x,\qquad u'''=-\cos x,\qquad u^{(4)}=\sin x
$$

> [!note] 注意
> $\sin x$ 求四阶导数恰好**回到自身**，这是特殊例子；一般函数并不会"转回来"。

## 9. 高阶导数的记号（Notations）

求导有多种写法，因此高阶导数也有多套等价记号；其中 $D$ 和 $\dfrac{d}{dx}$ 都是作用在函数上的**微分算子（operators）**：

| 阶数    | 撇号记号 Prime   | 算子记号 $D$ | 莱布尼茨记号 Leibniz        | 算子幂记号                            |
| ----- | ------------ | -------- | --------------------- | -------------------------------- |
| 一阶    | $f'(x)$      | $Df$     | $\dfrac{df}{dx}$      | $\left(\dfrac{d}{dx}\right)f$    |
| 二阶    | $f''(x)$     | $D^2 f$  | $\dfrac{d^2 f}{dx^2}$ | $\left(\dfrac{d}{dx}\right)^2 f$ |
| 三阶    | $f'''(x)$    | $D^3 f$  | $\dfrac{d^3 f}{dx^3}$ | $\left(\dfrac{d}{dx}\right)^3 f$ |
| $n$ 阶 | $f^{(n)}(x)$ | $D^n f$  | $\dfrac{d^n f}{dx^n}$ | $\left(\dfrac{d}{dx}\right)^n f$ |

## 10. 经典例题：$D^n x^n$

求 $x^n$ 的第 $n$ 阶导数（$n=1,2,3,\ldots$）。**先算前几项找规律（look for a pattern）**：

$$
\begin{aligned}
Dx^n &= nx^{n-1}\\
D^2 x^n &= n(n-1)x^{n-2}\\
D^3 x^n &= n(n-1)(n-2)x^{n-3}\\
&\ \vdots\\
D^{n-1}x^n &= \bigl(n(n-1)(n-2)\cdots 2\bigr)x^1
\end{aligned}
$$

规律：每求导一次，$x$ 的幂次降 $1$，同时乘上求导前的幂次。再求导一次：

$$
D^n x^n = n(n-1)(n-2)\cdots 2\cdot 1
$$

连乘积 $n(n-1)(n-2)\cdots 2\cdot 1$ 记作 $n!$，称为 **$n$ 的阶乘（$n$ factorial）**。因此

$$
D^n x^n = n!
$$

> [!important] 两个必记结论
> 1. $x^n$ 的第 $n$ 阶导数是**常数** $n!$（该规律也是**数学归纳法 mathematical induction** 证明的基础）；
> 2. 常数的导数为 $0$，所以再求一次：$D^{n+1}x^n=0$。

---

## 11. Session 9–12 全部法则总表

| 法则 | 公式 | 来源 Session |
| --- | --- | --- |
| 幂法则 Power Rule | $(x^n)'=nx^{n-1}$（负指数同样成立） | S9–10 |
| 常数倍 / 和法则 | $(cu)'=cu'$；$(u+v)'=u'+v'$ | S9 |
| 乘法法则 Product Rule | $(uv)'=u'v+uv'$ | S9 |
| 除法法则 Quotient Rule | $\left(\dfrac{u}{v}\right)'=\dfrac{u'v-uv'}{v^2}$ | S9–10 |
| 倒数法则 Reciprocal Rule | $\left(\dfrac{1}{v}\right)'=-\dfrac{v'}{v^2}$ | S10 |
| 链式法则 Chain Rule | $\bigl(f(g(x))\bigr)'=f'(g(x))\,g'(x)$ | S11 |
| 高阶导数 Higher Derivatives | $D^n x^n=n!$，$D^{n+1}x^n=0$ | S12 |

---

## 12. 思维导图（Session 9–12）

![](./图片/lecture%204-1788879996160.svg)

# Problem 12

>  $\sin(x)$ 和 $\cos(x)$ 这两个函数满足 $f''(x) = -f(x)$。
>  你还能想到其他满足 $f''(x) = -f(x)$ 的函数吗？

如果你想到了 $f(x) = 0$，或者类似 $f(x) = a\cos(x) + b\sin(x)$ 这样的函数，那你做得非常好。

如果这两个想法你都没有想到，也不必气馁；具有这种性质的函数是很少见的。求解像 $f''(x) = -f(x)$ 这样的"微分方程"可能非常困难；MIT 开设了一整门关于微分方程的课程。
