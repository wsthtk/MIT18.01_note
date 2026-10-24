# 重点


# MIT 18.01SC Session 23–25 复习笔记
## 线性近似与二次近似（Linear and Quadratic Approximations）

> [!abstract] 单元概览
> 本讲正式开启 **Unit 2：微分的应用（Applications of Differentiation）** 的第一部分（Part A: Approximation and Curve Sketching）：
> - **Session 23**：从导数定义反向推导出**线性近似（Linear Approximation）**，其本质是用切线逼近曲线（局部线性化 Local Linearity）。以 $x_0 = 0$ 为基准点，构建五大基础函数近似库（$\sin x, \cos x, e^x, \ln(1+x), (1+x)^r$）。
> - **Session 24**：确立“曲线复杂、直线简单（Curves are hard, lines are easy）”的计算哲学。掌握**代数组合（Algebraic Combinations）**技巧，在乘积与商中合理忽略 $x^2$ 高阶项，并利用近似反向读取导数 $f'(0)$。结合爱因斯坦狭义相对论钟慢效应，剖析 GPS 卫星时钟校准中的**相对误差（Relative Error）**。
> - **Session 25**：指出切线无法感知“弯曲”的致命缺陷（如 $\cos x$ 在 $0$ 附近水平切线为 $1$），由此引入二阶导数构建**二次近似（Quadratic Approximation / 最佳拟合抛物线 Best-fit Parabola）**。严格证明系数 $\frac{1}{2}$ 的来源（匹配二阶导数 $Q''(0) = 2c = f''(0)$），并分析凹凸性对误差方向（欠估计/过估计）的影响。
>
> 主线一句话：**“曲线很硬，直线很软；切线抓斜率，抛物线校弯曲。”（Curves are Hard, Lines are Easy; Tangent matches slope, Parabola matches curvature.）**

---

## Session 23：线性近似（Linear Approximation）

### 1. 线性近似的核心公式与几何切线（Linear Approximation & Tangent Line）

在微积分中，任何光滑可导曲线在放大至足够局部时，都近似呈现为一条直线，这称为**局部线性化（Local Linearity）**。

一条曲线 $y = f(x)$ 在基准点 $x_0$ 处的切线方程为：

$$y = f(x_0) + f'(x_0)(x - x_0)$$

因此，在 $x$ 靠近 $x_0$（记作 $x \approx x_0$）的邻域内，切线是原函数 $f(x)$ 极佳的线性近似：

> [!important] 线性近似通用公式（必背）
> $$f(x) \approx f(x_0) + f'(x_0)(x - x_0)\qquad (x \approx x_0)$$

> ![](./图片/lecture%209-ses23-tangent.png)
> 图：切线作为曲线的局部线性近似（原函数 $y=f(x)$ 与切线 $y=b+a(x-x_0)$，切点为 $(x_0, f(x_0))$，斜率 $a=f'(x_0)$）。

### 2. 从导数定义“反向解读”线性近似

线性近似并非新法则，而是导数定义的另一种等价表述。回顾导数定义：

$$f'(x_0) = \lim_{\Delta x \to 0}\frac{\Delta f}{\Delta x} = \lim_{\Delta x \to 0}\frac{f(x_0 + \Delta x) - f(x_0)}{\Delta x}$$

当改变量 $\Delta x$ 足够微小时（$\Delta x \approx 0$），我们可以去掉极限符号，得到近似关系：

$$\frac{\Delta f}{\Delta x} \approx f'(x_0)$$

这表明：**平均变化率（Average Rate of Change $\frac{\Delta f}{\Delta x}$）近似等于瞬时变化率（Instantaneous Rate of Change $f'(x_0)$）**。

两边同乘 $\Delta x$：

$$\Delta f \approx f'(x_0)\Delta x$$

展开 $\Delta f = f(x) - f(x_0)$ 以及 $\Delta x = x - x_0$，即得：

$$f(x) - f(x_0) \approx f'(x_0)(x - x_0) \implies f(x) \approx f(x_0) + f'(x_0)(x - x_0)$$

### 3. 经典示例：$\ln x$ 在 $x_0 = 1$ 处的线性近似与换元法（Change of Variables）

设 $f(x) = \ln x$，由于 $\ln 0$ 无定义（$\lim_{x \to 0^+} \ln x = -\infty$），无法在 $0$ 处展开，选择基准点 $x_0 = 1$：
- $f(1) = \ln 1 = 0$
- $f'(x) = \frac{1}{x} \implies f'(1) = 1$

代入线性近似公式：

$$\ln x \approx \ln(1) + f'(1)(x - 1) = 0 + 1(x - 1) = x - 1$$

即：

$$\ln x \approx x - 1\qquad (x \approx 1)$$

> [!tip] 换元法技巧（Change of Variables）
> 令新变量 $u = x - 1$，则 $x = 1 + u$。当 $x \approx 1$ 时，显然有 $u \approx 0$。
> 将其代回上式：
> $$\ln(1 + u) \approx u\qquad (u \approx 0)$$
> 将符号换回习惯的 $x$：$\ln(1 + x) \approx x$（$x \approx 0$）。
> 这样便将非零基准点 $x_0 = 1$ 转换为标准的 $0$ 基准点近似！

### 4. 在 $x \approx 0$ 处的五大基础线性近似表（Standard Approximations）

在绝大多数工程与数学计算中，统一选取 **$x_0 = 0$** 作为标准基准点。通用公式简化为：

$$f(x) \approx f(0) + f'(0)x\qquad (x \approx 0)$$

通过计算各函数在 $x = 0$ 处的数值与导数：

| 函数 $f(x)$ | 导函数 $f'(x)$ | $f(0)$ | $f'(0)$ | 线性近似公式（$x \approx 0$） |
| :--- | :--- | :---: | :---: | :--- |
| $\sin x$ | $\cos x$ | $0$ | $1$ | $\sin x \approx x$ |
| $\cos x$ | $-\sin x$ | $1$ | $0$ | $\cos x \approx 1$ |
| $e^x$ | $e^x$ | $1$ | $1$ | $e^x \approx 1 + x$ |
| $\ln(1+x)$ | $\frac{1}{1+x}$ | $0$ | $1$ | $\ln(1+x) \approx x$ |
| $(1+x)^r$ | $r(1+x)^{r-1}$ | $1$ | $r$ | $(1+x)^r \approx 1 + rx$ |

> [!important] 核心公式速查（必须熟练记忆）
> $$
> \begin{aligned}
> \sin x &\approx x \\
> \cos x &\approx 1 \\
> e^x &\approx 1 + x \\
> \ln(1+x) &\approx x \\
> (1+x)^r &\approx 1 + rx
> \end{aligned}\qquad (x \approx 0)
> $$

> ![](./图片/lecture%209-ses23-sincos.png)
> 图：(a) $\sin x$ 在原点处的切线近似 $y = x$；(b) $\cos x$ 在原点处的水平切线近似 $y = 1$（水平线无法感知向下弯曲趋势）。

> [!warning] 避坑警示：基准点选取与大数陷阱
> 近似公式仅在基准点 $x \approx x_0$ 的极小局部成立。若要估算 $\sin(1000)$，**绝不能盲目代入 $\sin x \approx x$ 得出 $1000$**（正弦函数被严格界定在 $[-1, 1]$）！
> 正确做法是利用周期 $2\pi$ 先规约到临近已知基准点（如 $318\pi \approx 999.03$），再做局部展开。

---

## Session 24：线性近似的技巧与应用（Examples & Applications）

### 1. 核心计算哲学：曲线很难，直线很容易（Curves are Hard, Lines are Easy）

为什么要用近似？
例如计算 $\ln(1.1)$：
- 直接计算 $\ln(1.1)$ 需要复杂的对数算法或查表，属于“困难计算”；
- 采用线性近似 $\ln(1 + x) \approx x$，直接代入 $x = 0.1$，立即可得 $\ln(1.1) \approx 0.1$，属于“简易计算”。

线性近似的核心价值在于：**在精度允许的局部范围内，用极其简单的多项式（一次式）替代高度复杂的先验函数（超越函数、分式根式等），从而极大地提速问题求解与系统建模**。

### 2. 代数组合技巧与“舍弃高阶项”（Algebraic Combinations）

对于复合的复杂函数，通常**不需要**对原函数求出庞大复杂的导数，而是利用基础近似公式在代数上直接组合，并**舍去 $x^2$ 及更高阶项**。

#### 典例：计算 $f(x) = \frac{e^{-3x}}{\sqrt{1+x}}$ 在 $x \approx 0$ 处的线性近似

**步骤 1**：将分式化为乘积与幂的形式：

$$f(x) = e^{-3x}(1+x)^{-1/2}$$

**步骤 2**：分别套用基础展开式：
- 对 $e^{-3x}$：套用 $e^u \approx 1 + u$，令 $u = -3x$，得 $e^{-3x} \approx 1 - 3x$；
- 对 $(1+x)^{-1/2}$：套用 $(1+x)^r \approx 1 + rx$，其中 $r = -\frac{1}{2}$，得 $(1+x)^{-1/2} \approx 1 - \frac{1}{2}x$。

**步骤 3**：相乘展开并略去高阶无穷小：

$$f(x) \approx (1 - 3x)\left(1 - \frac{1}{2}x\right) = 1 - \frac{1}{2}x - 3x + \frac{3}{2}x^2 = 1 - \frac{7}{2}x + \frac{3}{2}x^2$$

因为 $x \approx 0$，高阶项 $x^2$ 的量级比 $x$ 小得多（例如当 $x = 0.01$ 时，$x^2 = 0.0001$，$\frac{3}{2}x^2 = 0.00015$），在线性精度下一律舍去：

$$\boxed{f(x) \approx 1 - \frac{7}{2}x\qquad (x \approx 0)}$$

> [!tip] 反向读导数神技（Shortcut for Finding Derivatives）
> 线性近似的标准形式为 $f(x) \approx f(0) + f'(0)x$。
> 比对我们刚刚算出的 $1 - \frac{7}{2}x$：
> - 常数项 $f(0) = 1$
> - 一次项系数就是导数！直接读出：$\mathbf{f'(0) = -\frac{7}{2}}$！
> 
> 这意味着：**我们完全跳过了商法则（Quotient Rule）与乘积法则（Product Rule）的冗长微分过程，纯靠代数展开直接求得了 $f'(0)$**！

### 3. 理论支撑：两个线性近似乘积的线性部分（Product Rule Verification）

> [!note] 讲义练习题精要（Exercise 24）
> 设 $f(x)$ 与 $g(x)$ 在 $x_0$ 附近可导。
> - 直接近似相乘：
>   $$\begin{aligned}
>   \left[f(x_0) + f'(x_0)\Delta x\right]\left[g(x_0) + g'(x_0)\Delta x\right] &= f(x_0)g(x_0) + \left[f'(x_0)g(x_0) + f(x_0)g'(x_0)\right]\Delta x \\
>   &\quad + f'(x_0)g'(x_0)(\Delta x)^2
>   \end{aligned}$$
> - 对乘积函数 $H(x) = f(x)g(x)$ 直接求线性近似：
>   $$H(x) \approx H(x_0) + H'(x_0)\Delta x = f(x_0)g(x_0) + \left[f'(x_0)g(x_0) + f(x_0)g'(x_0)\right]\Delta x$$
> - 二者相差仅仅是 $f'(x_0)g'(x_0)(\Delta x)^2$，当 $\Delta x \approx 0$ 时完全可以忽略。
> 
> **结论**：复杂函数相乘时，先分别做线性近似再相乘舍弃高阶项，与对整体求导近似完全等价。

### 4. 物理与工程应用：狭义相对论钟慢效应与 GPS 卫星相对误差（Time Dilation & Relative Error）

> ![](./图片/lecture%209-ses24-satellite.png)
> 图：怪星 Planet Quirk 物理模型——地面观察者（me）与上空高速飞过的卫星（satellite，速度为 $v$）。

爱因斯坦狭义相对论指出，以速度 $v$ 运动的参考系内时钟（时标 $T$）与静止观察者腕表（时标 $T_m$）存在**时间膨胀（Time Dilation / 钟慢效应）**：

$$T_m = \frac{T}{\sqrt{1 - \frac{v^2}{c^2}}}$$

其中 $c \approx 3 \times 10^5\text{ km/s}$ 为光速。

#### （1）利用二项式近似化简
令无量纲小量 $u = \frac{v^2}{c^2}$，则分母为 $(1 - u)^{-1/2}$。利用 $(1 - u)^{-1/2} \approx 1 - \left(-\frac{1}{2}\right)u = 1 + \frac{1}{2}u$：

$$T_m = T\left(1 - \frac{v^2}{c^2}\right)^{-1/2} \approx T\left(1 + \frac{1}{2}\frac{v^2}{c^2}\right)$$

#### （2）计算相对误差（Relative Error / Percent Error）
时钟差异量为 $\Delta T = T_m - T$：

$$\Delta T = T_m - T \approx T\left(1 + \frac{1}{2}\frac{v^2}{c^2}\right) - T = \frac{1}{2}T\frac{v^2}{c^2}$$

由此得到相对误差公式：

> [!important] 相对误差公式
> $$\frac{\Delta T}{T} \approx \frac{1}{2}\frac{v^2}{c^2}$$
> 钟慢引起的相对百分比误差，直接正比于卫星速度与光速比值的平方 $\frac{v^2}{c^2}$。

#### （3）工程现实意义（GPS 校准）
GPS 卫星轨道速度 $v \approx 4\text{ km/s}$，则：

$$\frac{v^2}{c^2} \approx \left(\frac{4}{3 \times 10^5}\right)^2 \approx 1.8 \times 10^{-10} \implies \frac{\Delta T}{T} \approx 0.9 \times 10^{-10}$$

虽然看起来每秒只差 $10^{-10}$ 秒，但 GPS 依赖纳秒级（$10^{-9}\text{ s}$）电磁波测距（$1\text{ ns} \approx 0.3\text{ m}$）。若不对相对论效应进行线性近似校准，卫星定位每天将漂移数公里！工程人员正是利用该一阶近似对星载发射机频率进行了微调补偿。

---

## Session 25：二次近似导论（Quadratic Approximation）

### 1. 为什么需要二次近似？（曲率与切线的局限）

线性近似仅仅利用了一阶导数（斜率 Slope），其几何本质是一条**没有弯曲度的平直切线**。
例如考查 $f(x) = \cos x$ 在 $x = 0$ 处：
- $f(0) = 1, f'(0) = 0$；
- 线性近似为 $\cos x \approx 1$；
- 水平线 $y = 1$ 完全是一条死板的横线，根本反映不出 $\cos x$ 离开原点后**两侧向下弯曲**的特征。

为了更精确地捕捉函数的**弯曲形态（Curvature / 凹凸性）**，必须引入反映曲率与加速度的**二阶导数 $f''(x_0)$**，构造抛物线逼近。

### 2. 二次近似核心公式

设 $x \approx x_0$，函数 $f(x)$ 的二次近似是在线性近似后面追加一个含二阶导数的二次项：

> [!important] 二次近似公式（必背）
> $$f(x) \approx f(x_0) + f'(x_0)(x - x_0) + \frac{1}{2}f''(x_0)(x - x_0)^2\qquad (x \approx x_0)$$
> 其中：
> - $f(x_0) + f'(x_0)(x - x_0)$ 为**线性部分（Linear Part）**；
> - $\frac{1}{2}f''(x_0)(x - x_0)^2$ 为**二次校正项（Quadratic Correction Term）**。

### 3. 为什么系数前面必须有 $\frac{1}{2}$？（待定系数推导）

**数学解释**：二次近似的目标是在点 $x_0$ 处构造一阶、二阶导数均与原函数完美匹配的最佳多项式。

以 $x_0 = 0$ 为例，设逼近多项式为抛物线 $Q(x) = a + bx + cx^2$。
我们要求 $Q(x)$ 与原函数 $f(x)$ 满足三大匹配条件：
1. **数值匹配**：$Q(0) = f(0)$
   $$Q(0) = a \implies a = f(0)$$
2. **斜率匹配（一阶导匹配）**：$Q'(0) = f'(0)$
   $$Q'(x) = b + 2cx \implies Q'(0) = b \implies b = f'(0)$$
3. **曲率匹配（二阶导匹配）**：$Q''(0) = f''(0)$
   $$Q''(x) = 2c \implies Q''(0) = 2c \implies 2c = f''(0) \implies \mathbf{c = \frac{1}{2}f''(0)}$$

将求得的系数 $a, b, c$ 代回 $Q(x)$：

$$Q(x) = f(0) + f'(0)x + \frac{1}{2}f''(0)x^2$$

> [!note] 深刻理解那个 $\frac{1}{2}$
> 当对二次项 $cx^2$ 求导两次时，幂法则会掉下来一个指数：$\frac{d^2}{dx^2}(x^2) = 2$。
> 为了在求完两次导后抵消这个多出来的乘数 $2$、精确匹配目标二阶导 $f''(0)$，系数必须预先除以 $2$！这正是未来高阶泰勒级数中 $\frac{1}{n!}$ 的前身（$2 = 2!$）。

### 4. 经典实例：$\cos x$ 的最佳拟合抛物线（Best-fit Parabola）

对 $f(x) = \cos x$：
- $f(0) = \cos 0 = 1$
- $f'(x) = -\sin x \implies f'(0) = 0$
- $f''(x) = -\cos x \implies f''(0) = -1$

代入二次近似公式：

$$\cos x \approx 1 + 0 \cdot x + \frac{1}{2}(-1)x^2 = 1 - \frac{1}{2}x^2$$

> ![](./图片/lecture%209-ses25-cos-parabola.png)
> 图：$\cos x$ 的二次近似——黑色余弦曲线与红色最佳拟合抛物线 $1 - \frac{1}{2}x^2$（曲率高度贴合）。

### 5. 在 $x \approx 0$ 处的五大基础二次近似表

计算各函数在 $x = 0$ 处的一阶与二阶导数值：

| 函数 $f(x)$ | $f'(x)$ | $f''(x)$ | $f(0)$ | $f'(0)$ | $f''(0)$ | 二次近似公式（$x \approx 0$） |
| :--- | :--- | :--- | :---: | :---: | :---: | :--- |
| $\sin x$ | $\cos x$ | $-\sin x$ | $0$ | $1$ | $0$ | $\sin x \approx x$ |
| $\cos x$ | $-\sin x$ | $-\cos x$ | $1$ | $0$ | $-1$ | $\cos x \approx 1 - \frac{1}{2}x^2$ |
| $e^x$ | $e^x$ | $e^x$ | $1$ | $1$ | $1$ | $e^x \approx 1 + x + \frac{1}{2}x^2$ |
| $\ln(1+x)$ | $\frac{1}{1+x}$ | $-\frac{1}{(1+x)^2}$ | $0$ | $1$ | $-1$ | $\ln(1+x) \approx x - \frac{1}{2}x^2$ |
| $(1+x)^r$ | $r(1+x)^{r-1}$ | $r(r-1)(1+x)^{r-2}$ | $1$ | $r$ | $r(r-1)$ | $(1+x)^r \approx 1 + rx + \frac{r(r-1)}{2}x^2$ |

> [!important] 核心二次近似表（必须熟练掌握）
> $$
> \begin{aligned}
> \sin x &\approx x \\
> \cos x &\approx 1 - \frac{1}{2}x^2 \\
> e^x &\approx 1 + x + \frac{1}{2}x^2 \\
> \ln(1+x) &\approx x - \frac{1}{2}x^2 \\
> (1+x)^r &\approx 1 + rx + \frac{r(r-1)}{2}x^2
> \end{aligned}\qquad (x \approx 0)
> $$

---

## 7. 线性 vs 二次速查对照表与思维导图

### 7.1 精度飞跃：以 $e^x$ 数值计算为例（Exercise 25 数据）

计算 $x = 0.01, 0.1, 1$ 时的数值对比：

| $x$ | 真实值（计算器） | 线性近似 $1 + x$ | 线性绝对误差 | 二次近似 $1 + x + \frac{1}{2}x^2$ | 二次绝对误差 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **$0.01$** | $1.010050167\dots$ | $1.01$ | $5.0 \times 10^{-5}$ | $1.010050000$ | **$1.7 \times 10^{-7}$**（极度精准） |
| **$0.1$** | $1.105170918\dots$ | $1.10$ | $5.2 \times 10^{-3}$ | $1.105000000$ | **$1.7 \times 10^{-4}$** |
| **$1.0$** | $2.718281828\dots$ | $2.00$ | $0.718$ | $2.500000000$ | $0.218$（远离基准点失效） |

> [!tip] 精度规律
> 1. 在极近距离（$x = 0.01$），二次近似比线性近似精度提高近 **$300$ 倍**！
> 2. 当自变量远离基准点（如 $x = 1.0$），多项式逼近必然失效，因为指数函数增长远快于任何二次抛物线。

---

## 总结：核心速查矩阵

| 函数模型 | 线性近似（一阶） | 二次近似（二阶） | 二次项校正特征 |
| :--- | :--- | :--- | :--- |
| $\sin x$ | $x$ | $x$ | 二阶导为 $0$，一阶即达二阶精度 |
| $\cos x$ | $1$ | $1 - \frac{1}{2}x^2$ | 水平切线无法感知弯曲，二次项补足下弯 |
| $e^x$ | $1 + x$ | $1 + x + \frac{1}{2}x^2$ | 二次项补偿上凸增长弧度 |
| $\ln(1+x)$ | $x$ | $x - \frac{1}{2}x^2$ | 二次项负号补偿渐趋平缓的减速 |
| $(1+x)^r$ | $1 + rx$ | $1 + rx + \frac{r(r-1)}{2}x^2$ | 广泛适于各种分式根式展开（如 $r=-\frac{1}{2}$） |

---

## 思维导图
![720](./图片/lecture%209-mindmap.svg)
