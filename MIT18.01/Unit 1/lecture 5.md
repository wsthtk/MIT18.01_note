# MIT 18.01SC Session 13–15 复习笔记
## 隐函数求导与反函数（Implicit Differentiation & Inverse Functions）

> [!abstract] 单元概览
> - **Session 13**：隐函数求导（implicit differentiation）的原理，并用它把幂法则（power rule）推广到有理指数（rational exponent）。
> - **Session 14**：例题精解：圆的切线斜率、含混合项的方程、二阶导数（second derivative）。
> - **Session 15**：用隐函数求导推导反函数（inverse function）的导数公式，进而得到 $\arctan x$、$\arcsin x$ 和 $\sqrt{x}$ 的导数。
>
> 主线一句话：**隐函数求导本质上就是链式法则（chain rule）**。

---

## Session 13：隐函数求导（Implicit Differentiation）

### 1. 显式与隐式

- **显式函数（explicit function）**：$y=f(x)$，$y$ 被单独解出。
- **隐式关系（implicit relation）**：形如 $F(x,y)=0$，例如单位圆 $x^2+y^2=1$。它一般不定义（单一）函数——一个 $x$ 对应两个 $y$；但在曲线上某点附近取一个**分支（branch）**，仍可把 $y$ 看作 $x$ 的函数。
- 几何直观：点沿曲线滑动时，$x$ 的变化迫使 $y$ 按**约束（constraint）**变化，因此 $\frac{dy}{dx}$ 有意义。

### 2. 求导方法

> [!tip] 隐函数求导三步
> 1. 方程两边同时对 $x$ 求导；凡遇到 $y$ 的函数，一律用链式法则：
> $$\frac{d}{dx}\,g(y)=g'(y)\,\frac{dy}{dx}$$
> 2. 把所有含 $y'$ 的项移到一边，其余项移到另一边。
> 3. 提出 $y'$ 并解出；必要时利用原方程化简。

口诀：**每求一个含 $y$ 的项，自动乘一个 $y'$**。

### 3. 有理指数幂法则（Rational Exponent Rule）

目标：证明对有理数 $a=\frac{m}{n}$（$m,n$ 为整数），幂法则仍然成立：
$$\frac{d}{dx}x^{a}=a\,x^{a-1}$$
设 $y=x^{m/n}$。分母 $n$ 迫使我们开 $n$ 次方，于是两边取 $n$ 次方消去根号：
$$y^{n}=x^{m}$$
两边对 $x$ 求导（左边用链式法则）：
$$n\,y^{n-1}y'=m\,x^{m-1}$$
解出 $y'$，再代回 $y=x^{m/n}$：
$$y'=\frac{m}{n}\cdot\frac{x^{m-1}}{y^{n-1}}=\frac{m}{n}\,x^{\frac{m}{n}-1}$$
> [!important] 结论
> $$\frac{d}{dx}x^{m/n}=\frac{m}{n}\,x^{\frac{m}{n}-1}$$
> 特例：$\dfrac{d}{dx}\sqrt[n]{x}=\dfrac{1}{n}x^{\frac{1}{n}-1}$。（该公式包含了 n 次根的求导）
> 注意：**求导之后**才允许把 $y$ 换回 $x^{m/n}$——求导之前我们还不会对它求导，这正是要绕这一圈的原因。

> [!note] a 不同取值时的推导过程回顾
> 当 $a \in \mathbb{N}$ 时：二项展开
> 当 $a \in \mathbb{Z}$ 时：商法则
> 当 $a \in \mathbb{Q}$ 时：隐函数求导

---

## Session 14：隐函数求导例题

### 1. 单位圆的切线斜率

方程 $x^2+y^2=1$，求点 $(x,y)$ 处切线（tangent line）的斜率（slope）。

**直接法（direct version）**：取上半圆，
$$y=\sqrt{1-x^2}=(1-x^2)^{1/2}$$
用链式法则（外层 $u^{1/2}$，内层 $u=1-x^2$）：
$$y'=\frac12(1-x^2)^{-1/2}\cdot(-2x)=-\frac{x}{\sqrt{1-x^2}}=-\frac{x}{y}$$
**隐式法（implicit version）**：不解 $y$，直接对原方程求导：
$$2x+2y\,y'=0\quad\Longrightarrow\quad y'=-\frac{x}{y}$$
> [!note]- 图像（待补充）
> 单位圆及其在点 $(x,y)$ 处的切线。半径斜率为 $\frac{y}{x}$，切线与之垂直，故斜率为 $-\frac{x}{y}$。

隐式法的优点：不必选分支、不必处理根号，一个公式对整圆各点都成立（分母为 $0$ 时切线竖直）。

### 2. 例：$y^{4}+xy^{2}-2=0$

若显式求解，需把方程看成关于 $y^2$ 的二次方程，结果出现 $4$ 个分支，非常繁琐。直接隐式求导：
$$4y^3y'+\bigl(y^2+2xy\,y'\bigr)=0$$
$$(4y^3+2xy)\,y'=-y^2$$
$$\boxed{\,y'=-\frac{y^2}{4y^3+2xy}\,}$$
> [!warning] 注意
> 对 $xy^2$ 要用**乘积法则（product rule）**：$\dfrac{d}{dx}(xy^2)=y^2+x\cdot 2y\,y'$。

### 3. 二阶导数：椭圆 $x^{2}+4y^{2}=1$（自测例）

第一次求导：
$$2x+8y\,y'=0\quad\Longrightarrow\quad y'=-\frac{x}{4y}$$
> [!tip] 经验
> 求二阶导数之前，**先解出 $y'$ 再求导**，通常比直接再隐式求导更省事。

用商法则（quotient rule）对 $y'=-\dfrac{x}{4y}$ 求导：
$$y''=\frac{-4y+4x\,y'}{16y^2}=\frac{-y+x\,y'}{4y^2}$$
代入 $y'=-\dfrac{x}{4y}$，最后用原方程 $x^2+4y^2=1$ 化简：
$$y''=\frac{-x^2-4y^2}{16y^3}=\boxed{-\frac{1}{16y^3}}$$
> [!warning] 易错点
> - 若选择直接对 $2x+8yy'=0$ 再求导一次，会得到 $2+8y\,y''+8(y')^2=0$，其中 $(y')^2$ 项极易漏掉。
> - 算完务必用**原方程**把结果化到最简。
>
> **几何检验**：在椭圆顶点 $(0,\frac12)$ 处 $y'=0$（切线水平）；在 $(1,0)$ 处 $y'$ 无定义（切线竖直），均与图像一致。

### 4. 双曲线 $y^{2}-x^{2}=1$（自测例）
$$2y\,y'-2x=0\quad\Longrightarrow\quad y'=\frac{x}{y}$$
检验：$y=-1$ 时 $x=0$，切线水平；$x=1$ 时 $y=\pm\sqrt2$，斜率为 $\pm\dfrac{1}{\sqrt2}$，与图像吻合。

---

## Session 15：隐函数求导与反函数

### 1. 反函数（Inverse Function）

若 $g(f(x))=x$，则 $g$ 是 $f$ 的反函数，记作 $g=f^{-1}$；同时 $f=g^{-1}$。

- 例：$f(x)=\sqrt{x}$ 与 $g(x)=x^2$（限 $x>0$）互为反函数。
- 图像关系：把 $f$ 图像上每个点的 $x,y$ 坐标互换，即**关于直线 $y=x$ 对称（reflection across $y=x$）**。

> [!note]- 图像（待补充）
> $f(x)=\sqrt{x}$ 与 $f^{-1}(x)=x^2$（$x>0$）的图像关于直线 $y=x$ 对称。

### 2. 反函数求导公式

设 $y=f(x)$，即 $x=f^{-1}(y)$。对等式 $f^{-1}(y)=x$ 两边关于 $x$ 求导：
$$\frac{d}{dy}f^{-1}(y)\cdot\frac{dy}{dx}=1$$
于是
$$\boxed{\frac{dx}{dy}=\frac{1}{\,dy/dx\,}}\qquad\text{即}\qquad (f^{-1})'(y)=\frac{1}{f'(x)}$$
换成常见的以 $x$ 为自变量的写法：
$$\frac{d}{dx}f^{-1}(x)=\frac{1}{f'\!\left(f^{-1}(x)\right)}$$
> [!note] 直观与条件
> 反函数图像的切线斜率等于原函数切线斜率的**倒数**。前提是 $f'(x)\neq 0$（此时原切线水平，反函数切线竖直，导数不存在）。

### 3. $\arctan x$ 的导数

设 $y=\tan^{-1}x=\arctan x$，即 $\tan y=x$。两边对 $x$ 求导：
$$\sec^2 y\cdot y'=1\quad\Longrightarrow\quad y'=\cos^2 y$$
需要换回 $x$。由 $\tan y=x$ 作直角三角形：对边为 $x$、邻边为 $1$、斜边为 $\sqrt{1+x^2}$，故
$$\cos y=\frac{1}{\sqrt{1+x^2}}$$
$$\boxed{\frac{d}{dx}\arctan x=\frac{1}{1+x^2}}$$
> [!note]- 图像（待补充）
> $\tan x$ 在 $\left(-\frac{\pi}{2},\frac{\pi}{2}\right)$ 上由 $-\infty$ 增至 $+\infty$；关于 $y=x$ 反射得到 $\arctan x$：**定义域（domain）**为 $\mathbb{R}$，**值域（range）**为 $\left(-\frac{\pi}{2},\frac{\pi}{2}\right)$，有两条**水平渐近线（horizontal asymptote）** $y=\pm\frac{\pi}{2}$。

### 4. $\arcsin x$ 的导数

设 $y=\sin^{-1}x=\arcsin x$，即 $\sin y=x$。两边对 $x$ 求导：
$$\cos y\cdot y'=1\quad\Longrightarrow\quad y'=\frac{1}{\cos y}$$
由恒等式 $\cos^2y+\sin^2y=1$ 并代入 $\sin y=x$：
$$\cos y=\sqrt{1-x^2}$$
$$\boxed{\frac{d}{dx}\arcsin x=\frac{1}{\sqrt{1-x^2}}}$$
> [!warning] 根号的正负号
> 这里取正号，是因为 $\arcsin$ 的**主值范围（principal value range）** $y\in\left[-\frac{\pi}{2},\frac{\pi}{2}\right]$ 上恒有 $\cos y\ge 0$。处理反函数时经常面临这种分支选择，拿不准就**画图**确认。

### 5. 平方根：反函数法练习

$f(x)=x^2$（$x>0$）的反函数 $y=\sqrt{x}$ 满足 $y^2=x$。隐式求导：
$$2y\,y'=1\quad\Longrightarrow\quad y'=\frac{1}{2y}=\boxed{\frac{1}{2\sqrt{x}}}$$
与直接用幂法则 $\dfrac{d}{dx}x^{1/2}=\dfrac12 x^{-1/2}$ 结果一致，可作为交叉验证。

---

## 总结

> [!important] 必背公式
> $$
> \begin{aligned}
> &\frac{d}{dx}x^{m/n} =\frac{m}{n}\,x^{\frac{m}{n}-1} \\
> &\frac{d}{dx}\arctan x =\frac{1}{1+x^2} \\
> &\frac{d}{dx}\arcsin x =\frac{1}{\sqrt{1-x^2}} \\
> \end{aligned}
> $$
> 反函数求导：$\dfrac{dx}{dy}=\dfrac{1}{\,dy/dx\,}$。

> [!danger] 三大陷阱
> 1. 对含 $y$ 的项求导后**忘记乘 $y'$**（链式法则因子）。
> 2. 反函数导数算出的是关于 $y$ 的式子，**忘记换回 $x$**。
> 3. $\arcsin$ 类型问题中，根号的**正负号不按值域分支判断**。

---

## 思维导图
![717](./图片/lecture%205-1790351706440.svg)

# Recition video 15 反余弦函数求导复习笔记

## 1. 函数基础性质


> [!info] $y = \arccos x$ 核心信息
> 
> 
> - **定义域**：$x \in [-1,\ 1]$
> - **值域**：$y \in [0,\ \pi]$
> - **单调性**：定义域内严格单调递减
> - **关键点**：$(-1,\ \pi)$、$\left(0,\ \frac{\pi}{2}\right)$、$(1,\ 0)$

---

## 2. 导数推导（隐函数求导法）

### 步骤1：反函数转化

设 $y = \arccos x$，根据反余弦定义，等价于：
$$\cos y = x$$
约束条件：$y \in [0,\ \pi]$，$x \in [-1,\ 1]$。

### 步骤2：两边对 $x$ 求导

左侧用**复合函数链式法则**，右侧导数为1：
$$\frac{d}{dx}(\cos y) = \frac{d}{dx}(x)$$
$$-\sin y \cdot \frac{dy}{dx} = 1$$

### 步骤3：解出导数形式

整理得：
$$\frac{dy}{dx} = -\frac{1}{\sin y}$$

### 步骤4：换回 $x$ 的表达式

由三角恒等式 $\sin^2 y + \cos^2 y = 1$，代入 $\cos y = x$：
$$\sin y = \sqrt{1 - \cos^2 y} = \sqrt{1 - x^2}$$


> [!note] 符号说明
> 因为 $y \in [0,\ \pi]$，在此区间内 $\sin y \ge 0$，因此开根号**只取正号**。

代入导数表达式，最终得到：
$$\frac{dy}{dx} = -\frac{1}{\sqrt{1 - x^2}}$$

---

## 3. 几何直观记忆


> [!tip] 直角三角形辅助法
> 若 $\theta = \arccos x$，即 $\cos\theta = x$，可构造斜边为 $1$、邻边为 $x$ 的直角三角形：
> 
> 
> - 邻边 = $x$，斜边 = $1$
> - 由勾股定理，对边 = $\sqrt{1 - x^2}$
> 
> 
> 因此 $\sin(\arccos x) = \sin\theta = \frac{\text{对边}}{\text{斜边}} = \sqrt{1 - x^2}$，和恒等式推导完全一致。

---

## 4. 最终结论

> [!important] 核心求导公式
> $$\frac{d}{dx} \arccos x = -\frac{1}{\sqrt{1 - x^2}},\quad x \in (-1,\ 1)$$
> 
> 
> 补充：端点 $x=\pm1$ 处导数不存在（切线垂直于x轴）。

> [!tip] 对比记忆
> 和反正弦导数对比：$(\arcsin x)' = \frac{1}{\sqrt{1-x^2}}$，二者仅差一个负号。
> 规律：**递减的反三角函数导数为负，递增的为正**。