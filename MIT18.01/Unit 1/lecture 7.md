# 重点

# MIT 18.01SC Session 21 复习笔记
## 考试一复习：求导法则总览（Exam 1 Review）

> [!abstract] 单元概览
> 本讲是 **Exam 1 复习课（Review for Exam 1）**，不引入新知识，而是把 Session 1–20 的求导工具串成一张"考纲清单"：
> - **通用法则**：和、数乘、乘积、商、链式法则（chain rule）。
> - **具体公式**：必须背熟并能现场推导 $x^n,\sin x,\cos x,\tan x,\sec x,e^x,\ln x,\sin^{-1}x,\tan^{-1}x$ 的导数。
> - **链式法则再审视**：解释"率为什么相乘"，并由此重新推出商法则。
> - **例题串讲**：$\sec x$ → $\ln(\sec x)$ → $(x^{10}+8x)^6$ → $e^{x\tan^{-1}x}$。
> - **两大考试视角**：① 把导数定义**反读**成极限；② 用隐函数求导**反推**反三角函数与 $\ln x$ 的公式；③ 切线与可微性的图像判断。
>
> 主线一句话：**考试不靠背推导，而考"拿到任意函数都能拆成基本法则去求导"的能力**。

---

## 1. 考试要求必背的导数公式

### 1.1 通用求导法则（General Formulas）

设 $u=u(x),v=v(x)$ 均可导：

$$(u+v)'=u'+v',\qquad (cu)'=cu'$$

$$(uv)'=u'v+uv'\qquad\text{（product rule 乘积法则）}$$

$$\left(\frac{u}{v}\right)'=\frac{u'v-uv'}{v^2}\qquad\text{（quotient rule 商法则）}$$

$$\frac{d}{dx}f\bigl(u(x)\bigr)=f'\bigl(u(x)\bigr)\cdot u'(x)\qquad\text{（chain rule 链式法则）}$$

### 1.2 必须背熟且能推导的具体公式

考试要求对下列函数，**既会背导数、也能用导数定义现场推出来**：

$$x^n,\quad \sin^{-1}x,\quad \tan^{-1}x,\quad \sin x,\quad \cos x,\quad \tan x,\quad \sec x,\quad e^x,\quad \ln x$$

汇总（复习速查）：

> [!important] 必背导数表
> $$
> \begin{aligned}
> &(x^n)'=nx^{n-1} &&(\sin x)'=\cos x &&(\cos x)'=-\sin x\\
> &(\tan x)'=\sec^2 x &&(\sec x)'=\sec x\tan x &&(e^x)'=e^x\\
> &(\ln x)'=\frac1x &&(\sin^{-1}x)'=\frac1{\sqrt{1-x^2}} &&(\tan^{-1}x)'=\frac1{1+x^2}
> \end{aligned}
> $$

推导 $\sin x,\cos x$ 时，必须用到两个"零号"极限：

$$\lim_{h\to0}\frac{\sin h}{h}=1,\qquad \lim_{h\to0}\frac{\cos h-1}{h}=0$$

> [!tip] 考试提示
> 老师明确说：**不要把每条推导都背下来**。要练的是"对任意给的函数（比如 $e^x$、$\frac1{x^2}$）都能从导数定义出发推"。当年我们是靠这两个极限 + $a^x$ 在 $x=0$ 处的斜率，才搭出整张公式表。

---

## 2. 链式法则为什么成立 & 商法则的另一种推导

### 2.1 "率相乘"的直观

设 $y=10x+b$，即 $y$ 的变化是 $x$ 的 $10$ 倍：$\frac{dy}{dx}=10$。
若 $x$ 本身又随 $t$ 变化，$x=5t+a$，即 $\frac{dx}{dt}=5$。

把 $x=5t+a$ 代回：

$$y=10(5t+a)+b=50t+10a+b\quad\Longrightarrow\quad \frac{dy}{dt}=50$$

> [!important] 链式法则的本质
> $$\frac{dy}{dt}=\frac{dy}{dx}\cdot\frac{dx}{dt}=10\cdot5=50$$
> 因为 $y$ 比 $x$ 快 $10$ 倍、$x$ 比 $t$ 快 $5$ 倍，所以 $y$ 比 $t$ 快 $50$ 倍——**变化率连乘**。

### 2.2 用链式法则重新推出商法则

商法则最"丑"，可以不背：把 $\frac1v$ 看成 $v^{-1}$，用幂法则 + 链式法则：

$$\left(\frac1v\right)'=(v^{-1})'=-v^{-2}\,v'=-\frac{v'}{v^2}$$

于是 $\frac uv=u\cdot v^{-1}$，用乘积法则：

$$\left(\frac uv\right)'=u'v^{-1}+u(-v^{-2}v')=\frac{u'v-uv'}{v^2}$$

> [!note] 那个负号从哪来
> 商法则分子里 $uv'$ 前面的负号，正是 $\frac{d}{dv}v^{-1}=-v^{-2}$ 带来的。理解了这条，商法则就不用死记。

---

## 3. 例题串讲：一条链式法则练到底

### 3.1 $\sec x$ 的导数

把 $\sec x=\frac1{\cos x}=(\cos x)^{-1}$，用链式法则：

$$\frac{d}{dx}\sec x=\frac{d}{dx}(\cos x)^{-1}=-(\cos x)^{-2}(-\sin x)=\frac{\sin x}{\cos^2 x}$$

整理成标准形式（避免分数与负指数）：

$$\boxed{\frac{d}{dx}\sec x=\sec x\tan x}$$

### 3.2 $\ln(\sec x)$ 的导数

用 $(\ln u)'=\frac{u'}u$（链式法则）：

$$\frac{d}{dx}\ln(\sec x)=\frac{(\sec x)'}{\sec x}=\frac{\sec x\tan x}{\sec x}=\boxed{\tan x}$$

> [!note] 历史花絮
> Napier 当年**先发明自然对数、后发现指数函数**，正是为了航海中快速乘算正弦/余弦——对数比指数早出现很多年。这条"奇怪"的 $\ln(\sec x)$ 并非炫技，而是对数最初的用途。

### 3.3 $(x^{10}+8x)^6$ 的导数

**千万不要**把它乘开展开。直接链式法则：

$$\frac{d}{dx}(x^{10}+8x)^6=6(x^{10}+8x)^5\cdot(10x^9+8)$$

> [!warning] 答卷形式
> 考试允许答案保留任何**正确**形式，**不要求强行化简**。除非题目明确要求化成多项式，否则链式法则展开式就是最佳答案——强行展开反而易错。

### 3.4 终极大例：$e^{x\tan^{-1}x}$

第一节课承诺过"最后能求导任何东西"。设内层是乘积 $uv$（$u=x,\ v=\tan^{-1}x$）：

$$\frac{d}{dx}e^{uv}=e^{uv}\frac{d}{dx}(uv)=e^{uv}(u'v+uv')$$

代回 $u'=1,\ v'=\frac1{1+x^2}$：

$$\boxed{\frac{d}{dx}e^{x\tan^{-1}x}=e^{x\tan^{-1}x}\left(\tan^{-1}x+\frac{x}{1+x^2}\right)}$$

> [!tip] 套路
> 见到 $e^{\text{复杂式子}}$，永远先把指数整体提出来（$e^{(\cdots)}$ 照抄），再对指数里的"乘积/商/复合"逐项求导。

---

## 4. 从导数定义"反读"极限

导数定义是本课程的中心：

$$f'(x)=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$$

> [!important] 双向阅读
> 这个等式**正着读**是"用极限求导数"；**反着读**是"把认得出的极限直接换成导数值"。

**例**：求 $\displaystyle\lim_{u\to0}\frac{e^u-1}{u}$。

认出它就是 $f(x)=e^x$ 在 $x=0$ 处的导数定义（令 $\Delta x=u$）：

$$\lim_{u\to0}\frac{e^u-1}{u}=\left.\frac{d}{du}e^u\right|_{u=0}=e^0=\boxed{1}$$

> [!tip] 识别模板
> 看到 $\lim_{h\to0}\frac{\text{某式}-(\text{该式在一点的值})}{h}$，就问自己：这是哪个函数在哪一点的导数？认出来，答案立刻到手。

---

## 5. 隐函数求导的考试用途

隐函数求导（implicit differentiation）的威力：不必把 $y$ 解成 $x$ 的函数，就能两边对 $x$ 求导。

**回顾例题**（Session 13 型）：$y^3+3xy^2=8$，两边对 $x$ 求导：

$$3y^2y'+6xy\,y'+3y^2=0\quad\Longrightarrow\quad y'=\frac{-3y^2}{3y^2+6xy}$$

注意结果里**同时含 $x$ 和 $y$**，这正是隐式形式的常态。

### 5.1 现场推导 $(\sin^{-1}x)'$

令 $y=\sin^{-1}x$，即 $\sin y=x$。后者比 $y=\sin^{-1}x$ 好求导得多。两边对 $x$ 求导：

$$\cos y\cdot y'=1\quad\Longrightarrow\quad y'=\frac1{\cos y}$$

由 $\sin y=x$ 构造直角三角形：对边 $=x$、斜边 $=1$，邻边 $=\sqrt{1-x^2}$，故 $\cos y=\sqrt{1-x^2}$。

> ![](./图片/lecture%207-triangle.svg)
> 图：由 $\sin y=x$ 构造直角三角形，得 $\cos y=\sqrt{1-x^2}$（取正号，因 $y\in[-\frac\pi2,\frac\pi2]$ 时 $\cos y\ge0$）。

代入即得：

$$\boxed{\frac{d}{dx}\sin^{-1}x=\frac1{\sqrt{1-x^2}}}$$

同理，考试也可能要求用隐函数求导推 $\ln x$（由 $e^y=x$ 两边求导得 $e^y y'=1$，即 $y'=\frac1x$）。

---

## 6. 切线与可微性（Tangent Lines & Differentiability）

几何上，**导数就是切线斜率（slope of tangent line）**。考试三类相关题：

1. 给函数求某点**切线方程**；
2. 由原函数图像**画出导函数 $y'$ 的图像**；
3. 从图像判断某点是否**可微（differentiable）**。

### 6.1 可微的图像判据

> [!important]
> 函数可微 ⟺ 每一点都能画出唯一切线 ⟺ **割线从左侧逼近与从右侧逼近的极限相同**。
> 反之，尖点（cusp）、角点（corner）、竖直切线、间断点处都不可微。

### 6.2 练手：由 $y=\ln x$ 画 $y'=\frac1x$

老师给的练习：先画 $y=\ln x$，多画几条切线，观察斜率——它们**恒为正、越往右越平缓、没有斜率为 0 的点、$x\to0^+$ 时最陡**。把这些"斜率高度"转画成曲线，就是 $y'=\frac1x$。

> ![](./图片/lecture%207-ln-derivative.svg)
> 图：左 $y=\ln x$ 的切线斜率恒正且递减；右把斜率作为高度画出，正是 $y'=\frac1x$（红点 $x=1$ 处斜率 $=1$）。

> [!warning]
> **导函数的图像不必长得像原函数**！画完务必用公式 $\frac{d}{dx}\ln x=\frac1x$ 验算一遍。

---

## 总结

> [!important] 考试前必背
> $$
> \begin{aligned}
> &(uv)'=u'v+uv',\qquad \left(\frac uv\right)'=\frac{u'v-uv'}{v^2}\\
> &\frac{d}{dx}f(u(x))=f'(u)\,u'(x)\\
> &(\sec x)'=\sec x\tan x,\qquad (\tan x)'=\sec^2 x\\
> &(\ln\sec x)'=\tan x,\qquad (\sin^{-1}x)'=\frac1{\sqrt{1-x^2}},\qquad (\tan^{-1}x)'=\frac1{1+x^2}\\
> &\lim_{u\to0}\frac{e^u-1}{u}=1,\qquad \lim_{h\to0}\frac{\sin h}{h}=1
> \end{aligned}
> $$

> [!danger] 三大失分点
> 1. 拿到 $e^{\text{复杂式}}$ 时，**忘记把指数整体照抄**，只对指数局部求导。
> 2. 求 $(\sin^{-1}x)'$ 时，**忘记由直角三角形把 $\cos y$ 换回 $\sqrt{1-x^2}$**，结果停在 $\frac1{\cos y}$。
> 3. 画导函数图像时**凭感觉乱画**，以为它要长得像原函数；画完不用公式验算。

---

## 思维导图
![717](./图片/lecture%207-mindmap.svg)
