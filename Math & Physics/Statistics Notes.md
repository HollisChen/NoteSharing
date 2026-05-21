# Statistics Notes

## Basic Concepts

### Basics

(1) **Sample**: a sample is often considered a subset of data drawn from a population.

(2) **Duality of a sample**: 

- Before sampling: The sample is a set of random variables with uncertainty.
- After sampling: The sample becomes a set of fixed numbers, representing real data.

Suppose we want to draw a sample $X = \{X_1, X_2, \dots, X_n\}$ from a population. Before sampling,  $X_1, X_2, \dots, X_n$ are random variables with unknown values. After sampling, $X_1, X_2, \dots, X_n$ become specific values, say $x = \{x_1, x_2, \dots, x_n\}$. These fixed numbers can then be used to compute statistics like the sample mean or variance.

(3) **Statistic**: a statistic is a numerical characteristic of a sample that can be used to estimate a population parameter. 

(4) **Duality of a statistic**: like a sample, a statistic is a function (random variable) before sampling and a numerical value after sampling.

Examples of common statistics:

- **Sample Mean** ($\overline{X}$): the average of the sample values. Used to estimate the population mean ($\mu$).
$$
  \overline{X} = \frac{1}{n} \sum_{i=1}^n X_i
$$

- **Sample Variance** ($S^2$): A measure of how much the sample values vary. Used to estimate the population variance ($\sigma^2$).
$$
  S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \overline{X})^2
$$

(5) **Statistic vs. Parameter**:

- A **statistic** is calculated from the sample to describe or estimate something about the population. For examples, sample mean ($\overline{X}$), sample variance $S^2$.
- A **parameter** is a fixed value that describes some aspect of the entire population but is typically unknown. For examples, sample mean ($\mu$), sample variance ($\sigma^2$).

(6) **P-value** is a random variable.

(7) **Borel**: /bɔːˈrɛl/; **Lebesgue**: /ləˈbeɪɡ/.

### 重要积分公式

**1. Gamma function / Gamma 积分**

最标准形式：

$$
\Gamma(\alpha)=\int_0^\infty x^{\alpha-1}e^{-x}\,dx,\qquad \alpha>0
$$

当 $\alpha=n+1$，且 $n$ 是非负整数时：

$$
\int_0^\infty x^n e^{-x}\,dx=\Gamma(n+1)=n!
$$

在最常用的实数情形下，我们通常取 $\alpha>0$，$\alpha$ 是 Gamma 函数的输入变量；如果推广到复数，通常把输入变量写成 $z$：

$$
\Gamma(z)=\int_0^\infty x^{z-1}e^{-x}\,dx,
$$

此时这个积分定义要求 $\operatorname{Re}(z)>0$。通过解析延拓，$\Gamma(z)$ 可以进一步定义到几乎整个复平面，但 $0,-1,-2,\dots$ 这些非正整数点除外。直观地说，在这些点附近积分会在 $x=0$ 处发散，而且解析延拓后这些点仍然是无法去掉的极点（poles）。

具体来说，**Gamma 函数积分性质与推导总结**如下：

**核心总结**：Gamma 函数的半整数积分本质上与标准高斯积分同源（参见下一小节高斯积分部分），而其整数积分则是阶乘在连续实数域上的拓展。

* **整数点的积分（阶乘推导）**：
    利用分部积分法求解 $\Gamma(\alpha+1)$，可得核心递推公式 $\Gamma(\alpha+1) = \alpha\Gamma(\alpha)$。结合基准值 $\Gamma(1)=1$，通过数学归纳法即可轻松证明当 $\alpha$ 为正整数 $n$ 时，$\Gamma(n) = (n-1)!$。
* **半整数点的积分（结合高斯分布）**：
    计算基准点 $\Gamma(1/2)$ 时，通过简单的平方换元（令 $x=z^2$），即可将其积分式直接转化为标准高斯积分的右半部分，得出 $\Gamma(1/2)=\sqrt{\pi}$。对于 1.5, 2.5 等其他半整数，直接套用上述递推公式即可（如 $\Gamma(1.5) = 0.5 \cdot \Gamma(0.5)$）。
* **输入参数 $\alpha$ 的取值限制（复数与负数域）**：
    * **积分收敛条件**：最原始的积分定义式仅在 **$\alpha$ 的实部大于 0** 时成立。
    * **负数与复数求值**：对于实部小于 0 的数，积分本身不成立（会发散），但通过“解析延拓”（即利用公式 $\Gamma(\alpha) = \Gamma(\alpha+1)/\alpha$ 倒推），可以求出除禁忌点外所有负数和复数的值。比如你想算 $\Gamma(-0.5)$，虽然不能积分，但我可以代入公式：$\Gamma(-0.5) = \frac{\Gamma(0.5)}{-0.5}$。因为 $\Gamma(0.5) = \sqrt{\pi}$ 刚才已经算出来了，所以 $\Gamma(-0.5) = -2\sqrt{\pi}$。如果我想算 $\Gamma(0)$ 怎么办？代入公式就是 $\Gamma(0) = \frac{\Gamma(1)}{0}$，分母变成了 0，直接无意义！同理，推算 $\Gamma(-1)$ 时会用到 $\Gamma(0)$，也是无意义。
    * **无定义的极点**：$\alpha$ 绝对不能等于 **0, -1, -2, -3...（非正整数）**。在这些点上分母为 0，函数值发散至无穷大。

**补充：复数域与负数域的 Gamma 积分计算原则**

* **参数为复数时的直接计算**：
  如果 $\alpha$ 或 $\beta$ 是复数，只要满足积分的收敛条件（如实部大于 $0$），Gamma 积分就完全成立。在数学处理上，直接按复数积分法则硬算即可，算出来是啥就是啥（结果为一个确定的复数）。

* **$\alpha$ 实部为负数时的处理（解析延拓）**：
  如果 $\alpha$ 的实部是负数，原始的积分定义式会发散无法计算。此时，在数学上通过**解析延拓**技术——即利用递推公式 $\Gamma(\alpha) = \frac{\Gamma(\alpha+1)}{\alpha}$ 不断倒推，依然可以求出其对应的准确数值。此法则对整个复平面适用，唯独排除了 $0, -1, -2 \dots$ 这些非正整数极点（在这些点无定义）。

* **复数 $\beta$ 与柯西积分定理 (Cauchy's Integral Theorem)**：
  当参数 $\beta$ 为复数时，要证明广义公式  依$\int_0^\infty \beta^\alpha x^{\alpha-1} e^{-\beta x} dx = \Gamma(\alpha)$然成立，不能直接使用普通的实数换元法，而必须依赖**柯西积分定理**。
  * **柯西积分定理简述**：在复平面内，如果一个复变函数在某个闭合区域内处处“解析”（极其平滑且没有奇点），那么沿着该闭合路径绕行一圈的总积分必定恒等于 $0$。
  * **证明逻辑**：利用“绕一圈为 $0$”的特性，可以推导出路径形变原理——只要不跨越奇点，积分值就与路径无关。因此，证明中可以将原本沿实数轴的积分路径，合法地等价替换为复平面上的倾斜射线，从而严格证明该公式在复数域下同样成立。

---

**2. Gaussian integral / 高斯积分**

最标准形式：

$$
\int_{-\infty}^{\infty} e^{-x^2}\,dx=\sqrt{\pi}
$$

更一般的形式：

$$
\int_{-\infty}^{\infty} e^{-a x^2}\,dx=\sqrt{\frac{\pi}{a}},\qquad a>0
$$

**补充：与 Gamma 函数的内在联系**
标准高斯积分本质上等同于 Gamma 函数在输入参数 $\alpha=1/2$ 时的特例。只需对 $\Gamma(1/2)$ 的定义式进行简单的平方换元（令 $x = z^2$），即可得到 $\Gamma(1/2) = \int_{-\infty}^{\infty} e^{-z^2} dz = \sqrt{\pi}$，且这两种形式的解析解求解都依赖于相同的极坐标二重积分技巧。

---

**3. Dirichlet integral / 狄利克雷积分**

标准形式：

$$
\int_0^\infty \frac{\sin x}{x}\,dx=\frac{\pi}{2}
$$

### Poisson, Exponential, Gamma, Chi-square distributions 的关系

**1. Poisson distribution（泊松分布）：固定时间内事件发生的次数**

Poisson distribution 通常来自 Poisson process（泊松过程）。

如果事件以稳定平均速率 $\lambda$ 发生，那么在时间区间 $[0,t]$ 内发生的事件次数记为：

$$
N(t)
$$

则：

$$
N(t)\sim \mathrm{Poisson}(\lambda t)
$$

其概率质量函数（PMF, probability mass function）是：

$$
P(N(t)=k)=\frac{(\lambda t)^k e^{-\lambda t}}{k!},\quad k=0,1,2,\dots
$$

其中：

- $\lambda$：rate / intensity，单位时间内平均发生次数
- $t$：时间长度
- $\lambda t$：在长度为 $t$ 的时间内平均发生次数

所以 Poisson distribution 回答的问题是：

$$
\text{给定时间 }t\text{，事件发生了几次？}
$$

例如：平均每分钟来 $\lambda=2$ 个顾客，那么 5 分钟内来的顾客数是：

$$
N(5)\sim \mathrm{Poisson}(10)
$$

因为：

$$
\lambda t=2\times 5=10
$$

---

**2. Exponential distribution（指数分布）：等第一次事件的时间**

在 Poisson process 中，第 1 次事件发生的等待时间记为：

$$
T_1
$$

则：

$$
T_1\sim \mathrm{Exponential}(\lambda)
$$

指数分布的概率密度函数（PDF, probability density function）是：

$$
f(t)=\lambda e^{-\lambda t},\quad t>0
$$

其累积分布函数（CDF）是：

$$
F(t)=P(T_1\le t)=1-e^{-\lambda t}
$$

生存函数（survival function）是：

$$
P(T_1>t)=e^{-\lambda t}
$$

均值和方差是：

$$
E[T_1]=\frac{1}{\lambda}
$$

$$
\mathrm{Var}(T_1)=\frac{1}{\lambda^2}
$$

所以 Exponential distribution 回答的问题是：

$$
\text{从现在开始，等第 1 次事件发生要多久？}
$$

它和 Poisson distribution 的核心关系是：

$$
T_1>t
\iff
N(t)=0
$$

也就是说：

$$
\text{等第 1 次事件超过 }t
\iff
\text{在 }[0,t]\text{ 内一次事件都没有发生}
$$

因此：

$$
P(T_1>t)=P(N(t)=0)
$$

因为：

$$
N(t)\sim \mathrm{Poisson}(\lambda t)
$$

所以：

$$
P(N(t)=0)=\frac{(\lambda t)^0e^{-\lambda t}}{0!}=e^{-\lambda t}
$$

因此：

$$
P(T_1>t)=e^{-\lambda t}
$$

这就推出：

$$
T_1\sim \mathrm{Exponential}(\lambda)
$$

---

**3. Gamma distribution（伽马分布）：等第 $k$ 次事件的时间**

在 Poisson process 中，第 $k$ 次事件发生的时间记为：

$$
T_k
$$

它可以写成 $k$ 个独立指数等待时间的和：

$$
T_k=X_1+X_2+\cdots+X_k
$$

其中：

$$
X_i\overset{i.i.d.}{\sim}\mathrm{Exponential}(\lambda)
$$

所以：

$$
T_k\sim \mathrm{Gamma}(k,\lambda)
$$

这里使用的是 shape-rate 参数化：

$$
\text{shape}=k,\quad \text{rate}=\lambda
$$

Gamma distribution 的 PDF 是：

$$
f(t)=\frac{\lambda^\alpha}{\Gamma(\alpha)}t^{\alpha-1}e^{-\lambda t},\quad t>0
$$

其中：

- $\alpha$：shape parameter
- $\lambda$：rate parameter
- $\Gamma(\alpha)$：Gamma function

如果 $\alpha=k$ 是正整数，则：

$$
\Gamma(k)=(k-1)!
$$

所以当 $T_k\sim \mathrm{Gamma}(k,\lambda)$ 时：

$$
f_{T_k}(t)=\frac{\lambda^k}{(k-1)!}t^{k-1}e^{-\lambda t},\quad t>0
$$

均值和方差是：

$$
E[T_k]=\frac{k}{\lambda}
$$

$$
\mathrm{Var}(T_k)=\frac{k}{\lambda^2}
$$

所以 Gamma distribution 回答的问题是：

$$
\text{等第 }k\text{ 次事件发生要多久？}
$$

Exponential distribution 是 Gamma distribution 的特殊情况：

$$
\mathrm{Exponential}(\lambda)=\mathrm{Gamma}(1,\lambda)
$$

因为等第 1 次事件，就是等第 $k$ 次事件在 $k=1$ 的情况。

---

**4. Gamma function（伽马函数）和 Gamma distribution 的关系**

Gamma function 定义为：

$$
\Gamma(\alpha)=\int_0^\infty x^{\alpha-1}e^{-x}\,dx
$$

它满足递推关系：

$$
\Gamma(\alpha+1)=\alpha\Gamma(\alpha)
$$

对于正整数 $n$：

$$
\Gamma(n)=(n-1)!
$$

Gamma function 在 Gamma distribution 中的作用是 normalizing constant（归一化常数）。

因为：

$$
\int_0^\infty x^{\alpha-1}e^{-\lambda x}\,dx
=
\frac{\Gamma(\alpha)}{\lambda^\alpha}
$$

所以为了让概率密度积分等于 1，需要乘上：

$$
\frac{\lambda^\alpha}{\Gamma(\alpha)}
$$

因此 Gamma distribution 的 PDF 是：

$$
f(x)=\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\lambda x}
$$

一句话总结：

$$
\text{Gamma function 是用来把 }x^{\alpha-1}e^{-\lambda x}\text{ 归一化成概率密度的工具。}
$$

---

**5. Gamma distribution 的 shape-scale 写法**

Gamma distribution 也常用 shape-scale 参数化：

$$
X\sim \mathrm{Gamma}(\alpha,\theta)
$$

其中：

- $\alpha$：shape parameter
- $\theta$：scale parameter

PDF 是：

$$
f(x)=\frac{1}{\Gamma(\alpha)\theta^\alpha}x^{\alpha-1}e^{-x/\theta},\quad x>0
$$

均值和方差是：

$$
E[X]=\alpha\theta
$$

$$
\mathrm{Var}(X)=\alpha\theta^2
$$

rate 和 scale 是倒数关系：

$$
\lambda=\frac{1}{\theta}
$$

$$
\theta=\frac{1}{\lambda}
$$

所以：

$$
\mathrm{Gamma}(\alpha,\lambda)\text{ in shape-rate form}
$$

等价于：

$$
\mathrm{Gamma}\left(\alpha,\theta=\frac{1}{\lambda}\right)\text{ in shape-scale form}
$$

---

**6. Chi-square distribution（卡方分布）：标准正态平方和**

如果：

$$
Z_1,Z_2,\dots,Z_\nu \overset{i.i.d.}{\sim} N(0,1)
$$

那么：

$$
X=Z_1^2+Z_2^2+\cdots+Z_\nu^2
$$

服从 chi-square distribution with $\nu$ degrees of freedom：

$$
X\sim \chi^2_\nu
$$

其 PDF 是：

$$
f(x)=\frac{1}{2^{\nu/2}\Gamma(\nu/2)}x^{\nu/2-1}e^{-x/2},\quad x>0
$$

均值和方差是：

$$
E[X]=\nu
$$

$$
\mathrm{Var}(X)=2\nu
$$

Chi-square distribution 是 Gamma distribution 的特殊情况：

$$
\chi^2_\nu \sim \mathrm{Gamma}\left(\frac{\nu}{2},\frac{1}{2}\right)
$$

这里使用的是 shape-rate 参数化：

$$
\text{shape}=\frac{\nu}{2},\quad \text{rate}=\frac{1}{2}
$$

如果使用 shape-scale 参数化，则：

$$
\chi^2_\nu \sim \mathrm{Gamma}\left(\frac{\nu}{2},2\right)
$$

也就是说：

$$
\text{Chi-square distribution 是特殊的 Gamma distribution。}
$$

---

**7. 两个标准正态平方和与指数分布的关系**

如果：

$$
Z_1,Z_2\overset{i.i.d.}{\sim}N(0,1)
$$

那么：

$$
Z_1^2+Z_2^2\sim \chi^2_2
$$

而：

$$
\chi^2_2\sim \mathrm{Gamma}\left(1,\frac{1}{2}\right)
$$

这里是 shape-rate 写法。

因为：

$$
\mathrm{Gamma}(1,\lambda)=\mathrm{Exponential}(\lambda)
$$

所以：

$$
\chi^2_2\sim \mathrm{Exponential}\left(\frac{1}{2}\right)
$$

也就是说：

$$
Z_1^2+Z_2^2\sim \mathrm{Exponential}\left(\frac{1}{2}\right)
$$

注意这里必须是两个 independent standard normal 的平方和：

$$
Z_1^2+Z_2^2
$$

不是“两个普通正态分布”的平方和。严格来说，需要：

$$
Z_1,Z_2\overset{i.i.d.}{\sim}N(0,1)
$$

如果是非标准正态，或者有相关性，这个结论就不直接成立。

---

**8. 四种分布之间的核心关系图**

Poisson process 是核心来源：

$$
\text{Poisson process with rate }\lambda
$$

从“固定时间”角度看：

$$
N(t)=\text{time }t\text{ 内事件发生的次数}
$$

于是：

$$
N(t)\sim \mathrm{Poisson}(\lambda t)
$$

从“固定次数”角度看：

$$
T_1=\text{等第 1 次事件的时间}
$$

于是：

$$
T_1\sim \mathrm{Exponential}(\lambda)
$$

更一般地：

$$
T_k=\text{等第 }k\text{ 次事件的时间}
$$

于是：

$$
T_k\sim \mathrm{Gamma}(k,\lambda)
$$

而 Chi-square distribution 是 Gamma distribution 的特殊情况：

$$
\chi^2_\nu\sim \mathrm{Gamma}\left(\frac{\nu}{2},\frac{1}{2}\right)
$$

特别地：

$$
\chi^2_2\sim \mathrm{Gamma}\left(1,\frac{1}{2}\right)
=
\mathrm{Exponential}\left(\frac{1}{2}\right)
$$

所以：

$$
Z_1^2+Z_2^2\sim \mathrm{Exponential}\left(\frac{1}{2}\right)
$$

where:

$$
Z_1,Z_2\overset{i.i.d.}{\sim}N(0,1)
$$

---

**9. 最简总结**

Poisson distribution：

$$
N(t)\sim \mathrm{Poisson}(\lambda t)
$$

表示：

$$
\text{固定时间内发生几次事件}
$$

Exponential distribution：

$$
T_1\sim \mathrm{Exponential}(\lambda)
$$

表示：

$$
\text{等第 1 次事件要多久}
$$

Gamma distribution：

$$
T_k\sim \mathrm{Gamma}(k,\lambda)
$$

表示：

$$
\text{等第 }k\text{ 次事件要多久}
$$

Chi-square distribution：

$$
\chi^2_\nu\sim \mathrm{Gamma}\left(\frac{\nu}{2},\frac{1}{2}\right)
$$

表示：

$$
\nu\text{ 个独立标准正态变量平方和}
$$

特殊关系：

$$
\mathrm{Exponential}(\lambda)=\mathrm{Gamma}(1,\lambda)
$$

$$
\chi^2_\nu=\mathrm{Gamma}\left(\frac{\nu}{2},\frac{1}{2}\right)
$$

$$
\chi^2_2=\mathrm{Exponential}\left(\frac{1}{2}\right)
$$

$$
Z_1^2+Z_2^2\sim \chi^2_2\sim \mathrm{Exponential}\left(\frac{1}{2}\right)
$$

### 为什么样本方差除以 $n-1$：无偏性与 chi-square 分布

**1. 基本设定**

假设：

$$
X_1,\dots,X_n\overset{i.i.d.}{\sim}N(\mu,\sigma^2)
$$

样本均值：

$$
\bar X=\frac{1}{n}\sum_{i=1}^n X_i
$$

样本方差：

$$
s^2=\frac{1}{n-1}\sum_{i=1}^n(X_i-\bar X)^2
$$

核心问题是：为什么除以 $n-1$？

---

**2. 总平方和分解**

有一个**重要恒等式**：

$$
\sum_{i=1}^n(X_i-\mu)^2
=
\sum_{i=1}^n(X_i-\bar X)^2
+
n(\bar X-\mu)^2
$$

意思是：

$$
\text{围绕真实均值的总波动}
=
\text{围绕样本均值的波动}
+
\text{样本均值偏离真实均值的波动}
$$

所以：

$$
\sum_{i=1}^n(X_i-\bar X)^2
=
\sum_{i=1}^n(X_i-\mu)^2
-
n(\bar X-\mu)^2
$$

---

**3. 为什么是 $n-1$ 个自由度？**

因为样本偏差满足：

$$
\sum_{i=1}^n(X_i-\bar X)=0
$$

所以 $n$ 个偏差里只有 $n-1$ 个可以自由变化。

直觉上：

$$
\bar X
$$

是从数据中估计出来的，用掉了 1 个自由度。

因此：

$$
\sum_{i=1}^n(X_i-\bar X)^2
$$

只有 $n-1$ 个自由度。

---

**4. 无偏性：为什么 $E[s^2]=\sigma^2$**

由平方和分解：

$$
E\left[\sum_{i=1}^n(X_i-\bar X)^2\right]
=
E\left[\sum_{i=1}^n(X_i-\mu)^2\right]
-
E\left[n(\bar X-\mu)^2\right]
$$

第一项：

$$
E\left[\sum_{i=1}^n(X_i-\mu)^2\right]=n\sigma^2
$$

第二项：

$$
E\left[n(\bar X-\mu)^2\right]
=
n\mathrm{Var}(\bar X)
=
n\cdot\frac{\sigma^2}{n}
=
\sigma^2
$$

所以：

$$
E\left[\sum_{i=1}^n(X_i-\bar X)^2\right]
=
n\sigma^2-\sigma^2
=
(n-1)\sigma^2
$$

因此：

$$
E[s^2]
=
E\left[
\frac{1}{n-1}\sum_{i=1}^n(X_i-\bar X)^2
\right]
=
\sigma^2
$$

所以 $s^2$ 是 $\sigma^2$ 的 unbiased estimator。

---

**5. 更深一层：样本方差服从 scaled chi-square**

如果真实均值 $\mu$ 已知，那么：

$$
\sum_{i=1}^n\left(\frac{X_i-\mu}{\sigma}\right)^2
\sim \chi_n^2
$$

因为这是 $n$ 个 independent standard normal 的平方和。

但样本方差使用的是 $\bar X$，不是 $\mu$。估计 $\bar X$ 用掉 1 个自由度，所以：

$$
\frac{\sum_{i=1}^n(X_i-\bar X)^2}{\sigma^2}
\sim \chi_{n-1}^2
$$

由于：

$$
(n-1)s^2=\sum_{i=1}^n(X_i-\bar X)^2
$$

所以：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

也就是：

$$
s^2\sim \frac{\sigma^2}{n-1}\chi_{n-1}^2
$$

---

**6. 无偏不等于没有随机性**

$E[s^2]=\sigma^2$ 只说明平均来说估计对了。

但 $s^2$ 本身还是 random variable，它的分布是：

$$
s^2\sim \frac{\sigma^2}{n-1}\chi_{n-1}^2
$$

因此它也有自己的 variance。

因为如果：

$$
U\sim\chi_\nu^2
$$

则：

$$
E[U]=\nu,\quad \mathrm{Var}(U)=2\nu
$$

所以：

$$
\mathrm{Var}(s^2)
=
\frac{2\sigma^4}{n-1}
$$

当 $n$ 越大时，$s^2$ 越稳定地接近 $\sigma^2$。

---

**7. 和 t-test 的关系**

one-sample t-test 中：

$$
T=\frac{\bar X-\mu}{s/\sqrt n}
$$

可以写成：

$$
T=
\frac{
\frac{\bar X-\mu}{\sigma/\sqrt n}
}{
s/\sigma
}
$$

其中：

$$
\frac{\bar X-\mu}{\sigma/\sqrt n}\sim N(0,1)
$$

而：

$$
\frac{s}{\sigma}
=
\sqrt{
\frac{\chi_{n-1}^2}{n-1}
}
$$

所以：

$$
T=
\frac{Z}{\sqrt{\chi_{n-1}^2/(n-1)}}
\sim t_{n-1}
$$

这就是为什么未知方差时，均值检验用 t distribution。

---

**8. 最简总结**

样本方差除以 $n-1$，是因为估计 $\bar X$ 用掉了 1 个自由度：

$$
\sum_{i=1}^n(X_i-\bar X)=0
$$

所以：

$$
E\left[\sum_{i=1}^n(X_i-\bar X)^2\right]=(n-1)\sigma^2
$$

因此：

$$
E[s^2]=\sigma^2
$$

更重要的是：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

所以 $s^2$ 不是固定等于 $\sigma^2$，而是一个 scaled chi-square random variable。

一句话：

$$
\boxed{
\text{除以 }n-1\text{ 是为了无偏；chi-square 分布描述了 }s^2\text{ 自己的随机性。}
}
$$

### One-sample test, two-sample test, and sampling distributions

**1. 核心问题：test statistic 在 $H_0$ 下服从什么分布？**

Hypothesis testing 的核心不是单纯看样本均值差多少，而是构造一个 test statistic，然后问：

$$
\text{如果 }H_0\text{ 成立，这个 statistic 应该服从什么分布？}
$$

一旦知道它在 $H_0$ 下的分布，就可以计算：

$$
\text{p-value}
$$

或者找到 critical value，从而决定是否 reject $H_0$。

常见的检验包括：

- one-sample test：一个样本均值和某个给定值比较
- two-sample test：两个总体均值比较
- variance test：检验方差
- ANOVA / F-test：比较多组均值，或者比较两个 variance-like quantities

这一整套背后的核心分布是：

$$
N(0,1),\quad \chi^2,\quad t,\quad F
$$

它们之间有非常紧密的关系。

---

**2. One-sample test：一个样本均值和给定值比较**

假设：

$$
X_1,\dots,X_n
$$

来自一个总体，均值为 $\mu$，方差为 $\sigma^2$。

我们想检验：

$$
H_0:\mu=\mu_0
$$

对应的样本均值是：

$$
\bar X=\frac{1}{n}\sum_{i=1}^n X_i
$$

样本方差是：

$$
s^2=\frac{1}{n-1}\sum_{i=1}^n (X_i-\bar X)^2
$$

注意这里除以的是 $n-1$，不是 $n$。这是因为我们用样本均值 $\bar X$ 估计了总体均值 $\mu$，所以损失了一个自由度。

如果总体是 normal，而且 $\sigma$ 已知，那么：

$$
Z=\frac{\bar X-\mu_0}{\sigma/\sqrt n}\sim N(0,1)
$$

如果总体是 normal，但是 $\sigma$ 未知，就用 $s$ 代替 $\sigma$：

$$
T=\frac{\bar X-\mu_0}{s/\sqrt n}\sim t_{n-1}
$$

这里用 $t$ 而不是 normal，是因为分母里的 $s$ 也是从样本估计出来的，它本身有随机性。

---

**3. Two-sample test：两个总体均值比较**

假设有两组独立样本：

$$
Y_{11},\dots,Y_{1n_1}
$$

来自总体 1，均值为 $\mu_1$，方差为 $\sigma_1^2$；

$$
Y_{21},\dots,Y_{2n_2}
$$

来自总体 2，均值为 $\mu_2$，方差为 $\sigma_2^2$。

我们通常想检验：

$$
H_0:\mu_1-\mu_2=0
$$

两组样本均值分别是：

$$
\bar Y_1=\frac{1}{n_1}\sum_{i=1}^{n_1}Y_{1i}
$$

$$
\bar Y_2=\frac{1}{n_2}\sum_{i=1}^{n_2}Y_{2i}
$$

两组样本方差分别是：

$$
s_1^2=\frac{1}{n_1-1}\sum_{i=1}^{n_1}(Y_{1i}-\bar Y_1)^2
$$

$$
s_2^2=\frac{1}{n_2-1}\sum_{i=1}^{n_2}(Y_{2i}-\bar Y_2)^2
$$

这里同样是除以 $n_1-1$ 和 $n_2-1$，因为每一组都用自己的样本均值估计了总体均值，所以每组各损失一个自由度。

---

**4. Two-sample test 情况一：$\sigma_1,\sigma_2$ 已知**

如果两个总体都是 normal，并且 $\sigma_1,\sigma_2$ 已知，那么：

$$
\bar Y_1-\bar Y_2
$$

服从 normal distribution，而且：

$$
E(\bar Y_1-\bar Y_2)=\mu_1-\mu_2
$$

$$
\mathrm{Var}(\bar Y_1-\bar Y_2)=\frac{\sigma_1^2}{n_1}+\frac{\sigma_2^2}{n_2}
$$

所以：

$$
Z=
\frac{(\bar Y_1-\bar Y_2)-(\mu_1-\mu_2)}
{\sqrt{\sigma_1^2/n_1+\sigma_2^2/n_2}}
\sim N(0,1)
$$

在 $H_0:\mu_1-\mu_2=0$ 下：

$$
Z=
\frac{\bar Y_1-\bar Y_2}
{\sqrt{\sigma_1^2/n_1+\sigma_2^2/n_2}}
\sim N(0,1)
$$

这里用 $Z$ distribution，是因为总体方差 $\sigma_1^2,\sigma_2^2$ 是已知常数，不需要从样本估计。

---

**5. Two-sample test 情况二：$\sigma_1=\sigma_2=\sigma$ 未知**

如果两个总体都是 normal，而且假设两个总体方差相等：

$$
\sigma_1^2=\sigma_2^2=\sigma^2
$$

但 $\sigma^2$ 未知，那么需要用 pooled sample variance 来估计共同方差。

两组样本方差是：

$$
s_1^2=\frac{1}{n_1-1}\sum_{i=1}^{n_1}(Y_{1i}-\bar Y_1)^2
$$

$$
s_2^2=\frac{1}{n_2-1}\sum_{i=1}^{n_2}(Y_{2i}-\bar Y_2)^2
$$

因为：

$$
(n_1-1)s_1^2=\sum_{i=1}^{n_1}(Y_{1i}-\bar Y_1)^2
$$

$$
(n_2-1)s_2^2=\sum_{i=1}^{n_2}(Y_{2i}-\bar Y_2)^2
$$

所以 pooled variance 是把两组的 squared deviations 加起来，再除以总自由度：

$$
s_p^2=
\frac{(n_1-1)s_1^2+(n_2-1)s_2^2}
{n_1+n_2-2}
$$

这里的逻辑是：

$$
(n_1-1)s_1^2+(n_2-1)s_2^2
$$

先把两个样本方差“还原”为两组各自的 sum of squared deviations，然后再合并。

分母是：

$$
n_1+n_2-2
$$

因为两个样本各自估计了一个均值，所以一共损失了两个自由度。

这时 test statistic 是：

$$
T=
\frac{\bar Y_1-\bar Y_2}
{s_p\sqrt{1/n_1+1/n_2}}
\sim t_{n_1+n_2-2}
$$

这里用 $t$ distribution，是因为共同方差 $\sigma^2$ 是未知的，需要用 $s_p^2$ 估计。

---

**6. Two-sample test 情况三：$\sigma_1^2,\sigma_2^2$ 未知且不相等**

如果两个总体方差未知，而且不假设它们相等，那么用 Welch two-sample t-test。

test statistic 是：

$$
T=
\frac{\bar Y_1-\bar Y_2}
{\sqrt{s_1^2/n_1+s_2^2/n_2}}
$$

它近似服从 $t$ distribution，自由度用 Welch-Satterthwaite approximation：

$$
df\approx
\frac{(s_1^2/n_1+s_2^2/n_2)^2}
{\frac{(s_1^2/n_1)^2}{n_1-1}+\frac{(s_2^2/n_2)^2}{n_2-1}}
$$

这个方法比 pooled t-test 更稳，因为它不要求：

$$
\sigma_1^2=\sigma_2^2
$$

实际数据分析里，如果不确定两组方差是否相等，Welch t-test 通常更安全。

---

**7. 样本量从小到大：什么时候用 normal，什么时候用 t？**

可以按照下面的逻辑记。

如果总体 normal，且 $\sigma$ 已知：

$$
Z=\frac{\bar X-\mu_0}{\sigma/\sqrt n}\sim N(0,1)
$$

这时样本量大小不是关键，因为这是 exact normal result。

如果总体 normal，但 $\sigma$ 未知：

$$
T=\frac{\bar X-\mu_0}{s/\sqrt n}\sim t_{n-1}
$$

这时小样本要用 $t$ distribution。

如果样本量很大，即使总体不是 normal，也可以用 central limit theorem：

$$
\bar X\approx N\left(\mu,\frac{\sigma^2}{n}\right)
$$

当 $n$ 很大时，$s$ 也会接近 $\sigma$，所以：

$$
\frac{\bar X-\mu}{s/\sqrt n}\approx N(0,1)
$$

因此大样本时，即使 $\sigma$ 未知，很多时候也可以用 normal approximation。

简单总结：

$$
\text{small sample + normal population + known }\sigma \Rightarrow Z
$$

$$
\text{small sample + normal population + unknown }\sigma \Rightarrow t
$$

$$
\text{large sample + normal or non-normal population} \Rightarrow Z\text{ approximation}
$$

---

**8. Normal distribution：均值检验的基础**

标准正态分布是：

$$
Z\sim N(0,1)
$$

它的 density 是：

$$
f(z)=\frac{1}{\sqrt{2\pi}}e^{-z^2/2},\quad -\infty<z<\infty
$$

很多 test statistic 都是把估计量标准化成：

$$
\frac{\text{estimate}-\text{null value}}{\text{standard error}}
$$

如果分母里的 standard error 是已知的，或者大样本下估计得很准，那么这个 statistic 通常服从或近似服从：

$$
N(0,1)
$$

所以 normal distribution 是均值检验的基础。

---

**9. Chi-square distribution：方差估计的基础**

如果：

$$
Z_1,\dots,Z_\nu\overset{i.i.d.}{\sim}N(0,1)
$$

那么：

$$
Z_1^2+\cdots+Z_\nu^2\sim \chi_\nu^2
$$

这就是 chi-square distribution with $\nu$ degrees of freedom。

其 density 是：

$$
f(x)=
\frac{1}{2^{\nu/2}\Gamma(\nu/2)}
x^{\nu/2-1}e^{-x/2},
\quad x>0
$$

它和 Gamma distribution 的关系是：

$$
\chi_\nu^2\sim \mathrm{Gamma}\left(\frac{\nu}{2},\frac{1}{2}\right)
$$

这里是 shape-rate 写法。

如果使用 shape-scale 写法，则：

$$
\chi_\nu^2\sim \mathrm{Gamma}\left(\frac{\nu}{2},2\right)
$$

chi-square distribution 在统计推断里非常重要，因为 sample variance 和 chi-square distribution 有直接关系。

如果：

$$
X_1,\dots,X_n\overset{i.i.d.}{\sim}N(\mu,\sigma^2)
$$

那么：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

其中：

$$
s^2=\frac{1}{n-1}\sum_{i=1}^n(X_i-\bar X)^2
$$

所以：

$$
(n-1)s^2=\sum_{i=1}^n(X_i-\bar X)^2
$$

这说明 sample variance 的随机性本质上来自 chi-square distribution。

---

**10. t distribution：normal 除以估计出来的 standard error**

t distribution 的定义可以写成：

$$
T=\frac{Z}{\sqrt{U/\nu}}
$$

其中：

$$
Z\sim N(0,1)
$$

$$
U\sim \chi_\nu^2
$$

并且 $Z$ 和 $U$ 独立。

那么：

$$
T\sim t_\nu
$$

这个定义直接解释了为什么 t-test 会出现。

对于 one-sample t-test：

$$
\frac{\bar X-\mu}{\sigma/\sqrt n}\sim N(0,1)
$$

同时：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

所以：

$$
\frac{\bar X-\mu}{s/\sqrt n}
=
\frac{Z}{\sqrt{\chi_{n-1}^2/(n-1)}}
\sim t_{n-1}
$$

直觉上：

$$
t=\frac{\text{normal quantity}}{\text{estimated standard error}}
$$

因为分母是估计出来的，所以它比 normal distribution 有更厚的尾巴，尤其在自由度小的时候更明显。

当自由度变大时：

$$
t_\nu \to N(0,1)
$$

所以大样本时 $t$ 和 normal 很接近。

---

**11. F distribution：两个 normalized chi-square 的比值**

F distribution 来自两个独立 chi-square random variables 的比值。

如果：

$$
U\sim \chi_{d_1}^2
$$

$$
V\sim \chi_{d_2}^2
$$

并且 $U,V$ 独立，那么：

$$
F=
\frac{U/d_1}{V/d_2}
\sim F_{d_1,d_2}
$$

这里有两个自由度：

$$
d_1=\text{numerator degrees of freedom}
$$

$$
d_2=\text{denominator degrees of freedom}
$$

F distribution 之所以有两个自由度，是因为它本质上是两个 chi-square quantities 的比值，而每个 chi-square 都有自己的自由度。

F-test 常见于：

- 比较两个总体方差
- ANOVA
- regression overall significance test

---

**12. 用 F distribution 比较两个方差**

如果两个总体都是 normal，并且：

$$
H_0:\sigma_1^2=\sigma_2^2
$$

样本方差分别是：

$$
s_1^2=\frac{1}{n_1-1}\sum_{i=1}^{n_1}(Y_{1i}-\bar Y_1)^2
$$

$$
s_2^2=\frac{1}{n_2-1}\sum_{i=1}^{n_2}(Y_{2i}-\bar Y_2)^2
$$

那么：

$$
\frac{(n_1-1)s_1^2}{\sigma_1^2}\sim \chi_{n_1-1}^2
$$

$$
\frac{(n_2-1)s_2^2}{\sigma_2^2}\sim \chi_{n_2-1}^2
$$

因此：

$$
\frac{\left(\frac{(n_1-1)s_1^2}{\sigma_1^2}\right)/(n_1-1)}
{\left(\frac{(n_2-1)s_2^2}{\sigma_2^2}\right)/(n_2-1)}
\sim F_{n_1-1,n_2-1}
$$

化简得到：

$$
\frac{s_1^2/\sigma_1^2}{s_2^2/\sigma_2^2}
\sim F_{n_1-1,n_2-1}
$$

在 $H_0:\sigma_1^2=\sigma_2^2$ 下：

$$
\frac{s_1^2}{s_2^2}\sim F_{n_1-1,n_2-1}
$$

所以比较两个方差时，用 F distribution。

---

**13. ANOVA 里的 F-test**

ANOVA 用来比较多组均值是否相等。

假设有 $k$ 组，总样本量是 $N$。原假设是：

$$
H_0:\mu_1=\mu_2=\cdots=\mu_k
$$

ANOVA 的核心 statistic 是：

$$
F=
\frac{MSB}{MSW}
$$

其中：

$$
MSB=\frac{SSB}{k-1}
$$

是 between-group mean square，表示组间变异；

$$
MSW=\frac{SSW}{N-k}
$$

是 within-group mean square，表示组内变异。

所以：

$$
F=
\frac{SSB/(k-1)}{SSW/(N-k)}
$$

在 $H_0$ 成立时：

$$
F\sim F_{k-1,N-k}
$$

这里：

$$
k-1
$$

是 numerator degrees of freedom，对应组间变异；

$$
N-k
$$

是 denominator degrees of freedom，对应组内变异。

ANOVA 的直觉是：

$$
\text{如果组间差异明显大于组内随机波动，那么 }F\text{ 会很大}
$$

所以 F-test 本质上是在问：

$$
\text{between-group variability 是否显著大于 within-group variability？}
$$

---

**14. t distribution 和 F distribution 的关系**

t distribution 和 F distribution 有一个非常重要的关系：

如果：

$$
T\sim t_\nu
$$

那么：

$$
T^2\sim F_{1,\nu}
$$

原因是：

$$
T=\frac{Z}{\sqrt{U/\nu}}
$$

其中：

$$
Z\sim N(0,1)
$$

$$
U\sim \chi_\nu^2
$$

所以：

$$
T^2=\frac{Z^2}{U/\nu}
$$

因为：

$$
Z^2\sim \chi_1^2
$$

所以：

$$
T^2=
\frac{\chi_1^2/1}{\chi_\nu^2/\nu}
\sim F_{1,\nu}
$$

因此，在只有两组比较的时候，ANOVA 的 F-test 和 two-sample t-test 是等价的：

$$
F=t^2
$$

---

**15. 这套 sampling distributions 的整体关系**

这一整套关系可以从 normal distribution 开始理解。

首先：

$$
Z\sim N(0,1)
$$

然后：

$$
Z^2\sim \chi_1^2
$$

多个独立标准正态平方和：

$$
\sum_{i=1}^{\nu}Z_i^2\sim \chi_\nu^2
$$

sample variance 和 chi-square distribution 相关：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

normal quantity 除以 estimated standard error：

$$
\frac{Z}{\sqrt{\chi_\nu^2/\nu}}\sim t_\nu
$$

两个 normalized chi-square 的比值：

$$
\frac{\chi_{d_1}^2/d_1}{\chi_{d_2}^2/d_2}\sim F_{d_1,d_2}
$$

所以这几种分布可以这样理解：

$$
\text{Normal: mean 的基础}
$$

$$
\text{Chi-square: variance 的基础}
$$

$$
\text{t: mean / estimated standard error}
$$

$$
\text{F: variance-like quantity 的比值}
$$

---

**16. 常见 test 总结表**

| 问题                                 | Statistic                                                    | 分布              |
| ------------------------------------ | ------------------------------------------------------------ | ----------------- |
| 一个均值，$\sigma$ 已知              | $\frac{\bar X-\mu_0}{\sigma/\sqrt n}$                        | $N(0,1)$          |
| 一个均值，$\sigma$ 未知，总体 normal | $\frac{\bar X-\mu_0}{s/\sqrt n}$                             | $t_{n-1}$         |
| 两个均值，$\sigma_1,\sigma_2$ 已知   | $\frac{\bar Y_1-\bar Y_2}{\sqrt{\sigma_1^2/n_1+\sigma_2^2/n_2}}$ | $N(0,1)$          |
| 两个均值，方差未知但相等             | $\frac{\bar Y_1-\bar Y_2}{s_p\sqrt{1/n_1+1/n_2}}$            | $t_{n_1+n_2-2}$   |
| 两个均值，方差未知且不等             | $\frac{\bar Y_1-\bar Y_2}{\sqrt{s_1^2/n_1+s_2^2/n_2}}$       | approximate $t$   |
| 一个方差                             | $\frac{(n-1)s^2}{\sigma_0^2}$                                | $\chi_{n-1}^2$    |
| 两个方差比较                         | $\frac{s_1^2}{s_2^2}$                                        | $F_{n_1-1,n_2-1}$ |
| 多组均值比较 ANOVA                   | $\frac{MSB}{MSW}$                                            | $F_{k-1,N-k}$     |
| 两组均值比较 ANOVA                   | $F$                                                          | $F=t^2$           |

---

**17. 最简总结**

如果总体方差已知，均值检验用 normal：

$$
Z\sim N(0,1)
$$

如果总体方差未知，均值检验用 t：

$$
T\sim t_{df}
$$

如果检验方差，用 chi-square：

$$
\frac{(n-1)s^2}{\sigma^2}\sim \chi_{n-1}^2
$$

如果比较两个方差型量，用 F：

$$
F=
\frac{\chi_{d_1}^2/d_1}{\chi_{d_2}^2/d_2}
\sim F_{d_1,d_2}
$$

整体逻辑是：

$$
\boxed{
\text{normal } \rightarrow \text{ chi-square } \rightarrow \text{ t and F}
}
$$

也就是说：

$$
\boxed{
\text{normal 处理均值，chi-square 处理方差，t 处理未知方差下的均值，F 处理两个方差型量的比值。}
}
$$

### Covariance vs Correlation Coefficient

**Covariance**

Covariance measures the **direction and strength of the linear relationship** between two random variables.

Definition:

$$
\operatorname{Cov}(X, Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]
$$

Interpretation:

- If $\operatorname{Cov}(X, Y) > 0$: X and Y increase or decrease together (positive correlation).  
- If $\operatorname{Cov}(X, Y) < 0$: when X increases, Y decreases (negative correlation).  
- If $\operatorname{Cov}(X, Y) = 0$: X and Y are linearly uncorrelated (but not necessarily independent).  

Limitation: Covariance values **depend on the measurement scale**. If you change temperature from °C to °F, or length from cm to m, the covariance value will change. Therefore, covariances between variables with different units are not directly comparable.

**Covariance Matrix Formula**

Let **$X$ be an $n \times d$ matrix**:  

- $n$: number of samples  
- $d$: number of features (variables)

The key matrix form of the covariance is:

$$
(X - \bar{X})^\top (X - \bar{X})
$$

This is the **core (unnormalized) form** of the covariance matrix. To obtain the actual covariance matrix, we divide by a normalization factor:
$$
\Sigma = \frac{1}{n - 1}(X - \bar{X})^\top (X - \bar{X})
$$

2. **$(X - \bar{X})$** is the *mean-centered* matrix (each column minus its mean).  
   - Each **row** represents the deviation of one sample from the mean.  
   - Each **column** represents all deviations of one variable.

3. The matrix product **$(X - \bar{X})^\top (X - \bar{X})$** gives a $d \times d$ matrix.  
   - Its $(i, j)$ entry equals  
     $$
     \sum_{k=1}^n (x_{k,i} - \bar{x}_i)(x_{k,j} - \bar{x}_j)
     $$
     — i.e., the sum of the cross-deviations between variables $i$ and $j$.

3. Dividing by $(n - 1)$ gives the **sample covariance**, while dividing by $n$ gives the **population covariance**.

| Type                             | Formula                                                  | Meaning                                                   |
| -------------------------------- | -------------------------------------------------------- | --------------------------------------------------------- |
| **Sample covariance matrix**     | $\Sigma = \frac{1}{n-1}(X - \bar{X})^\top (X - \bar{X})$ | Each entry is the sample covariance between two variables |
| **Population covariance matrix** | $\Sigma = \frac{1}{n}(X - \bar{X})^\top (X - \bar{X})$   | Used when the dataset is treated as the entire population |

Random vector form: Let $Z \in \mathbb{R}^d$ be a random vector with covariance matrix $\Sigma_Z = \operatorname{Cov}(Z)$. If $A \in \mathbb{R}^{m \times d}$ is a constant matrix, then

$$
\operatorname{Cov}(A Z) = A\,\Sigma_Z\,A^\top
$$

---

**Correlation Coefficient**

The **correlation coefficient** (also called the *Pearson correlation coefficient*) is the **standardized form** of covariance.

Definition:

$$
\rho_{XY} = \frac{\operatorname{Cov}(X, Y)}{\sigma_X \sigma_Y}
$$

where $\sigma_X = \sqrt{\operatorname{Var}(X)}$ and $\sigma_Y = \sqrt{\operatorname{Var}(Y)}$.

Properties:

- $-1 \leq \rho_{XY} \leq 1$  
- $\rho_{XY} > 0$: positive correlation  
- $\rho_{XY} < 0$: negative correlation  
- $\rho_{XY} = 0$: no linear correlation  

Advantages:

- **Unit-free** (dimensionless)  
- **Invariant to scale** — rescaling X or Y does not change $\rho$

**Comparison Table**

| Aspect            |            Covariance $\operatorname{Cov}(X,Y)$            |               Correlation $\rho(X,Y)$                |
| :---------------- | :--------------------------------------------------------: | :--------------------------------------------------: |
| Definition        |        $\mathbb{E}[(X-\mathbb{E}X)(Y-\mathbb{E}Y)]$        | $\dfrac{\operatorname{Cov}(X,Y)}{\sigma_X \sigma_Y}$ |
| Unit              |               Has units (depends on X and Y)               |                    Dimensionless                     |
| Range             |                    $(-\infty, +\infty)$                    |                      $[-1, 1]$                       |
| Meaning           | Direction and strength of linear relationship (with scale) |         Direction and strength (normalized)          |
| Scale Sensitivity |                 Sensitive to unit scaling                  |               Not affected by scaling                |
| Typical Use       |                   Covariance matrix, PCA                   | Correlation analysis, visualization (e.g. heatmaps)  |

💡 One-sentence Summary

> Covariance tells **whether two variables move together**, 
> while correlation tells **how strongly and consistently they move together**.

### Central Limit Theorem (CLT)

**1. Concept**

Regardless of the population's distribution, the **sampling distribution of the mean** becomes asymptotically normal as the sample size $n$ increases.

**2. Math**

Let $X_1, \dots, X_n$ be i.i.d. with mean $\mu$ and variance $\sigma^2$. As $n \to \infty$:
$$\sqrt{n}(\bar{X}_n - \mu) \xrightarrow{d} N(0, \sigma^2)$$

**3. Proof**

* **Tool:** Characteristic Function $\varphi_X(t) = E[e^{itX}]$.
* **Process:** 1. Express the characteristic function of the normalized sum.
    2. Use **Taylor Expansion** to approximate the function near zero.
    3. Take the limit as $n \to \infty$.
* **Result:** The limit is $e^{-t^2/2}$, which is the unique "fingerprint" of a standard normal distribution.

### 统计学中的四种收敛方式

关于依概率收敛和几乎处处收敛的理解，还可以参考这个视频[直观理解概率论里的“依概率收敛”“几乎处处收敛”“以分布收敛”](https://www.bilibili.com/video/BV1Lm4y1q7pQ)。

a.s. 收敛：看几乎每一条样本路径上，$X_n(ω)$ 是否趋近 $X(ω)$。

概率收敛：看 $X_n$ 和 $X$ 在同一个 $ω$ 下差很多的概率是否趋近 $0$。

分布收敛：不看 $X_n(ω)$ 和 $X(ω)$ 是否接近，只看 $X_n$ 的分布形状是否趋近 $X$ 的分布形状。也就是说，分布收敛只关心“随机变量取值的概率分布”，甚至不要求 $X_n$ 和 $X$ 来自同一个事件集合/样本空间。

---

**1. 依概率收敛 (Convergence in Probability, $\xrightarrow{P}$)**

这是统计学中最基础、最常用的收敛概念，关注的是**误差超过预定范围的可能性**。

- **定义**：对于任意微小的 $\epsilon > 0$：
  $$\lim_{n \to \infty} P(|X_n - X| > \epsilon) = 0$$
- **直观理解**：随着 $n$ 增大，虽然 $X_n$ 偶尔还会偏离目标 $X$，但偏离得“比较远”的可能性已经越来越微不足道了。
- **典型应用**：**弱大数定律 (WLLN)**。它保证了样本均值是总体均值的**一致估计量 (Consistent Estimator)**。

---

**2. 几乎处处收敛 / 以概率 1 收敛 (Almost Sure Convergence, $\xrightarrow{a.s.}$)**

这是更严格的收敛，关注的是**每一个样本路径 (Sample Path)** 的归宿。

- **定义**：
  $$P(\omega \in \Omega: \lim_{n \to \infty} X_n(\omega) = X(\omega)) = 1$$
- **直观理解**：
  - “依概率收敛”只保证在某个时刻 $n$ 犯错的概率小。
  - “几乎处处收敛”保证了在百分之百的平行宇宙里，序列 $X_1, X_2, \dots$ 最终都会**死死地钉在**目标 $X$ 上，永远不再离开。
- **关系**：如果 $X_n \xrightarrow{a.s.} X$，那么一定有 $X_n \xrightarrow{P} X$。反之则不一定（见后文反例）。
- **典型应用**：**强大数定律 (SLLN)**。

---

**3. $L^p$ 收敛 / $r$ 阶矩收敛 (Convergence in $L^p$ mean, $\xrightarrow{L^p}$)**

这种方式关注的是**平均误差的大小**。

- **定义**：
  $$\lim_{n \to \infty} E[|X_n - X|^p] = 0 \quad (\text{通常 } p \ge 1)$$
- **直观理解**：这是一种“能量”层面的要求。它不仅要求犯错概率小，还要求即便犯错，错误造成的平均损失（$p$ 次方的期望）也要趋于 0。
- **关系**：$L^p$ 收敛可以推导出依概率收敛。

---

**4. 依分布收敛 (Convergence in Distribution, $\xrightarrow{d}$)**

这是最宽松的收敛，它不关心随机变量本身的值，只关心其**概率分布的形状**。

**分布收敛不要求 $X_n$ 和 $X$ 在同一个样本点 $\omega$ 上有强关联。** 它主要比较的是：

$X_n$ 的分布形状是否越来越接近 $X$ 的分布形状。也就是说，看 cumulative distribution function（分布函数）：
$$
F_n(x)=P(X_n\le x)
$$

是否收敛到

$$
F(x)=P(X\le x)
$$

定义是：

$$
X_n \xrightarrow{d} X
$$

如果对所有 $F$ 的连续点 $x$，都有

$$
F_n(x)\to F(x)
$$

分布收敛只关心“随机变量取值的概率分布”，不看 $X_n(\omega)$ 和 $X(\omega)$ 是否逐点接近。甚至不要求 $X_n$ 和 $X$ 来自同一个事件集合/样本空间；只要它们的分布函数满足上面的收敛关系，就可以说 $X_n \xrightarrow{d} X$。

- **定义**：在目标分布 $F(x)$ 的每一个连续点上：
  $$\lim_{n \to \infty} F_n(x) = F(x)$$
- **直观理解**：$X_n$ 本身并没有变成 $X$，但 $X_n$ 表现出来的统计规律（如直方图）和 $X$ 一模一样。
- **典型应用**：**中心极限定理 (CLT)**。我们说样本均值标准化后收敛到标准正态分布，指的就是这种收敛。

---

**5. 几乎处处收敛 vs $L^p$ 收敛**

这两者之间没有绝对的强弱关系。

(1) $L^p \xrightarrow{\text{不一定}} a.s.$ (反例：打字机序列)

设 $X_n$ 是区间 $[0,1]$ 上的滑动窗口函数。窗口宽度 $1/k$ 趋于 0，但它会在区间上循环扫描（这个问题的具体定义需额外查询，如果你不知道哦啊，这里的定义可能看不懂）。
- **$L^p$ 视角**：窗口下面积为 $1/k \to 0$，平均误差趋于 0，**收敛**。
- **a.s. 视角**：对于区间内任意一点 $x$，随着窗口循环扫描，该点会反复被盖住（变为1）又被跳过（变为0）。该点的值始终在 $0, 1, 0, 1$ 震荡，无法稳定，**不收敛**。

(2) $a.s. \xrightarrow{\text{不一定}} L^p$ (反例：逃逸的尖峰)

设 $X_n$ 在概率为 $1/n^2$ 的情况下等于 $n^4$（极窄且极高的尖峰），其余情况为 $0$。
- **a.s. 视角**：根据Borel-Cantelli 第一引理，$A_n = \{X_n ≠ 0\}$ 只会发生有限多次。因此在几乎所有路径下，从某个 $n$ 开始，$X_n$ 都会永远保持为 0，**收敛**。（参见下方注释）
- **$L^p$ 视角**：期望 $E[X_n] = n^4 \times (1/n^2) = n^2$。随着 $n \to \infty$，平均偏离程度反而飞向了无穷大，**不收敛**。

注释：$\sum_{n=1}^{\infty}P(A_n)=\sum_{n=1}^{\infty}\frac{1}{n^2}=\frac{\pi^2}{6}<\infty,$$A_n$ 只会发生有限多次，即$P(A_n \text{ infinitely often})=0$，换句话说，几乎所有样本路径上，尖峰 $X_n=n^4$ 只会出现有限次。因此从某个随机的 $N(\omega)$ 开始，后面所有 $X_n(\omega)$ 都等于 0。注意概率为 $1/n$时不成立，因为$\sum_{n=1}^{\infty}\frac{1}{n}=\infty$，对于某个样本路径，可能存在不断的无限次出现非零值，不能满足几乎处处收敛。$a.s.$ 收敛不是只看每个单独的 $n$ 出现尖峰的概率是否变小，而是看一整条样本路径上，尖峰是否最终停止。如果尖峰无穷多次出现，即使每次概率很小，路径也不会收敛到 0。即：

$1/n^2$ 下降得极快 $\implies$ 概率和有限 $\implies$ 尖峰只出现有限次 $\implies$ 最终彻底归零 $\implies$ 几乎处处收敛。

$1/n$ 下降得太慢 $\implies$ 概率和无穷大 $\implies$ 尖峰出现无限次 $\implies$ 永远无法彻底归零 $\implies$ 不收敛。

---

**6. 收敛的“食物链”**

$$
X_n \xrightarrow{a.s.} X \implies X_n \xrightarrow{P} X \implies X_n \xrightarrow{d} X
$$

$$
X_n \xrightarrow{L^p} X \implies X_n \xrightarrow{P} X \implies X_n \xrightarrow{d} X
$$

注意：$X_n \xrightarrow{a.s.} X$ 和 $X_n \xrightarrow{L^p} X$ 之间一般没有推出关系。

*注意：如果收敛到的目标 $X$ 是一个常数，那么 $X_n \xrightarrow{d} c \iff X_n \xrightarrow{P} c$。*

### 不相关、独立与特征函数

**1. 不相关 vs 独立**

这是两个在“关系强度”和“适用范围”上完全不在一个层级的概念。

**不相关 (Uncorrelated)** 

* **定义：** 协方差为零，即 $Cov(X,Y) = 0$。
* **本质：** 仅仅排除了**线性关系**（即无法用一条直线拟合）。
* **局限性：** 不相关绝对不等于没有关系！它们私底下完全可以有极其强烈的**非线性关系**（例如经典的 $Y = X^2$ 完美抛物线，计算出来依然是不相关的）。
* **期望拆解能力：** 只能拆解最基础的线性乘积，即保证 $E[XY] = E[X] \cdot E[Y]$。一旦给变量套上非线性函数（如平方、指数），拆解立刻翻车。

**独立 (Independent)** 

* **定义：** 联合概率密度等于边缘概率密度的乘积，即 $f(x,y) = f(x) \cdot f(y)$。
* **本质：** 排除了**任何形式的关系**（不论线性还是非线性）。两个变量的结构是彻底解耦的（面团可以干净地切开两半）。
* **期望拆解能力：** 无论你使用多么复杂的非线性函数 $g()$ 和 $h()$，都永远保证 $E[g(X)h(Y)] = E[g(X)] \cdot E[h(Y)]$。

---

**2. 大数定律中的条件差异：切比雪夫 vs 辛钦**

为什么不同的定理对条件的要求不一样？完全取决于它们的证明工具。

* **切比雪夫大数定律（只要求“两两不相关”）：**
    * **前提：** 要求方差存在。
    * **原理：** 证明过程依赖于求和的方差展开式。方差展开只涉及到二阶矩（即协方差）。
    * **结论：** 既然数学工具是个“近视眼”，只能看到线性相关性（协方差），那么只要协方差为 0（不相关），交叉项就全部消掉了，证明就通了。它不需要独立的非线性保护。
* **辛钦大数定律（必须要求“相互独立”）：**
    * **前提：** 放弃了方差存在的条件（只要求期望存在）。
    * **原理：** 没有了方差，传统的方差展开法失效，被迫使用概率论核武器——**特征函数**。特征函数的乘法拆解必须要求独立性。

---

**3. 特征函数的降维打击与完备性**

**为什么要把变量放到指数上？**

* **几何视角：** 借助欧拉公式 $e^{itX} = \cos(tX) + i\sin(tX)$，相当于用不同频率（$t$）的正弦波和余弦波像雷达一样去扫描概率分布，求出它在复平面上的“重心”（本质就是对概率密度函数的傅里叶变换）。
* **代数视角（降维打击）：** 指数函数是唯一能把“加法”变成“乘法”的工具（$e^{A+B} = e^A \cdot e^B$）。它把多个随机变量相加极其难算的“卷积积分”，变成了简单的“特征函数连乘”。

**为什么特征函数的乘法必须要求独立？**

我们需要让：$$E[e^{it(X+Y)}] = E[e^{itX}] \cdot E[e^{itY}]$$
成立，这背后有两层原因：
* **非线性的暴露：** $e^{itX}$ 是包含 $\sin$ 和 $\cos$ 的极强非线性函数。“不相关”只能处理 $E[XY]$，处理不了非线性函数。只有“独立”能保证非线性函数的期望依然能完美拆开。
* **傅里叶基底的完备性（核心顿悟）：** 特征函数要求上述等式对**所有的频率 $t$** 都成立。在数学上，不同频率的正余弦波构成了函数空间的“完备基底”。如果两个变量在所有的正弦波频率上都能拆开（互不影响），就意味着它们在宇宙中任何非线性映射下都能拆开。**这种全方位的、毫无死角的无关系，就是“完全独立”的数学真谛！**

### 矩母函数 (Moment Generating Function) 与特征函数 (Characteristic Function)

在概率论与数理统计中，为了避免直接处理复杂的分布推导，数学家构造了两种极其强大的“变换工具”来分析随机变量 (Random Variable) 的叠加与分布特性。

为什么要“变换”？（加法、卷积与乘法的完美等价）

当我们研究两个独立随机变量的相加（即 $Z = X + Y$）时，求 $Z$ 的概率密度分布，本质上就是对 $X$ 和 $Y$ 的概率密度函数进行**标准的数学卷积 (Convolution)**。

* **解开“负号”的疑惑**：为什么是真正的标准卷积？因为 $Z = X+Y$，即 $Y = Z-X$。当我们遍历所有可能时，积分式为 $\int f_X(x) f_Y(Z-x) dx$，这里因移项产生的 $(Z-x)$，完美契合了标准卷积定义中的负号。
* **降维打击**：根据微积分与泛函分析的“卷积定理”，**时域（或空域）中的卷积，等于频域中的相乘**。因此，将概率分布转化为矩母函数或特征函数后，原本令人窒息的“概率卷积（积分）”运算，瞬间降维成了极度简单的小学生“多项式相乘”。

---

1. 矩母函数 (Moment Generating Function, MGF)

* **定义 (Definition)**：
    对于随机变量 $X$，其矩母函数定义为 $e^{tX}$ 的期望 (Expectation)：
    $$M_X(t) = E[e^{tX}]$$

* **核心意义 (Core Significance)**：
    * **矩的压缩包 (Moments Generator)**：它将分布的所有各阶矩打包在了一起。对 $M_X(t)$ 连续求 $k$ 次导数，并令 $t=0$，就能直接掉出 $X$ 的第 $k$ 阶原点矩 $E[X^k]$（如均值、方差、偏度等）。
    * **化加为乘 (Transforming Addition to Multiplication)**：利用指数 $e^{A+B} = e^A \cdot e^B$ 的特性，将多个独立变量相加后的复杂分布，转化为各自矩母函数的直接相乘。

* **致命缺陷 (Limitation)**：
    **不一定存在**。因为 $e^{tX}$ 增长得极快，对于某些具有厚尾/肥尾特性 (Heavy-tailed) 的分布（比如柯西分布 Cauchy Distribution，极端事件概率大），其期望的积分会发散到无穷大，导致矩母函数在此类场景下失效。

---

2. 特征函数 (Characteristic Function, CF)

* **定义 (Definition)**：
    引入复数域 (Complex domain) 的虚数单位 $i$ ($i^2 = -1$)，特征函数定义为 $e^{itX}$ 的期望：
    $$\varphi_X(t) = E[e^{itX}]$$

* **核心意义 (Core Significance)**：
    * **普遍存在 (Universal Existence)**：这是特征函数最大的王牌。因为根据欧拉公式，$|e^{itX}| = |\cos(tX) + i\sin(tX)| = 1$，它不再像 $e^{tX}$ 那样爆炸增长，而是永远变成了一个有界的波动圆环。所以**任何**合法的概率分布，其特征函数**绝对存在**且连续。
    * **数学本质 (Mathematical Nature)**：对于连续型随机变量，特征函数本质上就是其概率密度函数 (Probability Density Function, PDF) 的**傅里叶变换 (Fourier Transform)**。通过逆变换，我们可以从特征函数 100% 还原出原始分布。

---

3. 核心对比总结 (Key Comparisons)

| 维度 (Dimension)              | 矩母函数 (MGF)                              | 特征函数 (CF)                          |
| :---------------------------- | :------------------------------------------ | :------------------------------------- |
| **自变量空间 (Space)**        | 实数域 (Real domain)                        | 复平面 (Complex plane)                 |
| **变换类型 (Transform Type)** | 类似拉普拉斯变换 (Laplace Transform)        | 本质是傅里叶变换 (Fourier Transform)   |
| **存在性 (Existence)**        | 不一定存在 (Not always guaranteed)          | **永远存在 (Always exists)**           |
| **主要应用场景 (Use Cases)**  | 日常推导、直观求矩 (如中心极限定理初级证明) | 严谨的高阶理论证明、处理发散或厚尾分布 |

### 信息量（Information）和熵（Entropy）

在这份笔记中，我们将暂时剥离物理学背景，纯粹从概率与信息论的视角，系统梳理“信息量”与“熵”的底层逻辑。

**1. 信息量 (Information)：事件发生带来的“惊奇”**

在信息论中，衡量一条信息的价值，并不看它的篇幅长短，而是看它发生的概率有多低。

*   **核心理念**：**信息量（Information）等同于“惊奇度（Surprisal）”**。
*   **原理解析**：一个事件（尤其是所谓的“小事件”）发生的概率越小，它发生时带给我们的“惊奇”就越大，包含的信息量也就越大；反之，如果是早已100%确定的事，发生时毫不令人意外，其信息量就几乎为零。
*   **数学公式**：
    如果事件 $x$ 发生的概率为 $p(x)$，那么该事件的单个信息量 $I(x)$ 定义为其概率的负对数：
    $$I(x) = -\log p(x)$$
    *(注：公式完美契合了直觉——$p(x)$ 越小，$-\log p(x)$ 算出来的正值就越大，即小概率事件带来的信息量巨大。)*

---

**2. 熵 (Entropy)：系统的整体“未知”**

“信息量”衡量的是某个单一的具体事件，而“熵”衡量的是整个系统的宏观状态（例如一整局抛硬币游戏或整个随机变量的分布）。

*   **核心定义**：**熵的定义是：系统中所有可能发生事件的“信息量”的平均期望值（加权平均）。**
*   **本质概括**：**熵，就是系统内在的“未知程度”。**
*   **数学公式**：
    对于一个包含所有可能状态 $x$ 的离散系统，其系统总熵 $H$ 等于每个具体事件的信息量与其发生概率乘积的总和：
    $$H = -\sum p(x) \log p(x)$$

---

**3. 核心逻辑链条：从“未知”到“新知”**

理清信息论最关键的一步，是明白系统固有的“状态”与观测动作带来的“收获”之间的动态转化。这是一个此消彼长的过程。

请牢记以下这套核心逻辑推演链条：

> **熵越大 $\rightarrow$ 系统的“不确定性”越高 $\rightarrow$ 你在观测前拥有的信息越少 $\rightarrow$ 当结果揭晓时，你获取的“新信息量”越大。**

**对比辅助记忆**：
*   **低熵状态**（如一枚两面都是“正面”的作弊硬币）：系统内在的未知程度极低。你在观测前已经确信了结果，因此结果揭晓时，你没有感到任何惊奇，获取的“新信息量”为零。
*   **高熵状态**（如一枚绝对均匀的完美硬币）：系统内在的未知程度达到最大。你在观测前完全无法预测，因此在结果揭晓的那一刻，彻底消除了你的不确定性，你获取了巨大的“新信息量”。

### Kronecker Product

The **Kronecker product** of two matrices $A$ (size $m \times n$) and $B$ (size $p \times q$) is written as  
$$
A \otimes B =
\begin{bmatrix}
a_{11}B & a_{12}B & \dots & a_{1n}B\\
a_{21}B & a_{22}B & \dots & a_{2n}B\\
\vdots & \vdots & \ddots & \vdots\\
a_{m1}B & a_{m2}B & \dots & a_{mn}B
\end{bmatrix}
$$

The resulting matrix has size $(mp) \times (nq)$.

Intuitively, the Kronecker product describes **how two matrix structures interact** across different dimensions. 

It is widely used in linear algebra, signal processing, and statistics — for example, to build large covariance matrices that separate row and column dependencies.

### Cholesky decomposition

[Cholesky decomposition - Wikipedia](https://en.wikipedia.org/wiki/Cholesky_decomposition)

**1️⃣ Definition**

For any **real symmetric positive definite (SPD)** matrix $A \in \mathbb{R}^{n \times n}$, there exists a **unique lower-triangular matrix** $L$ with **positive diagonal entries** such that

$$
A = L\,L^\top.
$$

This is called the **Cholesky decomposition** (or factorization).

**2️⃣ Why “lower-triangular”?**

In theory, $A$ can also be written as $A = R^\top R$ where $R$ is upper-triangular. To make the factorization **unique**, we **fix the convention**:

> Always choose the **lower-triangular** form with positive diagonal entries.

This removes ambiguity (since both lower and upper versions are valid but equivalent under transposition).

**3️⃣ Uniqueness (Positive Definite Case)**

If $A$ is **positive definite** ($x^\top A x > 0$ for all $x \neq 0$): $L$ exists and is **invertible** and **unique**.

**4️⃣ Semi-definite Case (Rank-deficient / PSD)**

If $A$ is **positive semi-definite** (some eigenvalues = 0):

- $A$ can still be written as $A = L L^\top$, but $L$ is **not invertible** (some diagonal entries = 0).
- The decomposition is **not unique**, because within the nonzero-eigenvalue subspace (the "active covariance directions"), you can apply any orthogonal rotation $Q$ and still have
  
  $$
A = (LQ)(LQ)^\top.
  $$
  
- This reflects the **rotational freedom** in degenerate (zero-variance) directions.

**5️⃣ Geometric & Statistical View (Covariance Interpretation)**

If a random vector $z \sim \mathcal{N}(0, I)$ (zero-mean, unit covariance), and we define $x = Lz$, then

$$
\operatorname{Cov}(x) = L\,L^\top = A.
$$

So geometrically:
- $L$ is the **linear transformation** that maps a unit sphere into the **ellipsoid** with covariance $A$.
- For full-rank (SPD) $A$, this mapping is uniquely defined.
- For rank-deficient (PSD) $A$, some directions collapse (zero variance), and the ellipsoid degenerates into a **flat subspace** — within which the basis (orientation) can be freely rotated.

**6️⃣ Summary Table**

| Case                    | Geometric Shape                                   | Invertible? | Rotational Freedom      | Uniqueness   |
| ----------------------- | ------------------------------------------------- | ----------- | ----------------------- | ------------ |
| Positive Definite (SPD) | Full ellipsoid (all directions have variance)     | ✅ Yes       | ❌ None                  | ✅ Unique     |
| Semi-definite (PSD)     | Line / plane (collapsed along zero-variance axes) | ❌ No        | ✅ In the range subspace | ❌ Not unique |

**7️⃣ Relation to Covariance Matrices**

In multivariate statistics:
- Any covariance matrix $\Sigma$ is symmetric and PSD.
- If $\Sigma$ is SPD, the Cholesky factor $L$ gives a **unique “square root”** of $\Sigma$.
- If $\Sigma$ is rank-deficient, $L$ gives one of infinitely many square roots, all corresponding to the same covariance structure but different bases in the active subspace.

### Matrix Normal Distribution

A random matrix $X$ of size $n \times q$ follows a **matrix normal distribution** if  
$$
X \sim MN_{n \times q}(M, \Sigma, \Psi)
$$
which means  
$$
\mathrm{vec}(X) \sim N(\mathrm{vec}(M),\, \Psi \otimes \Sigma)
$$

Here:
- $M$ is the mean matrix  
- $\Sigma$ is the **row covariance** (an $n \times n$ matrix)  
- $\Psi$ is the **column covariance** (a $q \times q$ matrix)

The Kronecker product $\Psi \otimes \Sigma$ combines these two directions of covariance into one large covariance matrix for $\mathrm{vec}(X)$. 

The operator $\mathrm{vec}(\cdot)$ stacks the columns of a matrix into one long vector (a column vector of length $nq$ that lists all entries of $X$ **column by column**.):  

If  
$$
X =
\begin{bmatrix}
x_{11} & x_{12} & \dots & x_{1q}\\
x_{21} & x_{22} & \dots & x_{2q}\\
\vdots & \vdots & \ddots & \vdots\\
x_{n1} & x_{n2} & \dots & x_{nq}
\end{bmatrix},
$$
then  
$$
\mathrm{vec}(X) =
\begin{bmatrix}
x_{11}\\
x_{21}\\
\vdots\\
x_{n1}\\
x_{12}\\
x_{22}\\
\vdots\\
x_{nq}
\end{bmatrix}.
$$

**🧩 Deriving the Matrix Normal Distribution from a Standard Normal Matrix**

**Step 1️⃣. Linear transformation of a Gaussian**

If a random vector $z \sim N(0, I)$ (all entries are i.i.d. standard normal), then for any constant matrix $A$:

$$
x = A z \;\Rightarrow\; x \sim N(0,\, A A^\top).
$$

**Key fact:** A linear transformation of a Gaussian is still Gaussian — only its covariance changes to $A A^\top$.

**Step 2️⃣. Simple 2D example**

Let

$$
z = 
\begin{bmatrix}
z_1\\
z_2
\end{bmatrix}
\sim N(0, I_2),
\qquad
A =
\begin{bmatrix}
1 & 0\\
0.8 & 0.6
\end{bmatrix}.
$$

Then

$$
x = A z
\quad\Rightarrow\quad
\operatorname{Cov}(x) = A A^\top =
\begin{bmatrix}
1 & 0.8\\
0.8 & 1
\end{bmatrix}.
$$

The two coordinates of $x$ become correlated, but $x$ remains Gaussian.  

Hence: **“Gaussian + linear transform ⇒ still Gaussian.”**

**Step 3️⃣. Move from vectors to matrices**

Now consider a matrix of i.i.d. standard normals:

$$
Z =
\begin{bmatrix}
z_{11} & z_{12} & \dots & z_{1q}\\
z_{21} & z_{22} & \dots & z_{2q}\\
\vdots & \vdots & \ddots & \vdots\\
z_{n1} & z_{n2} & \dots & z_{nq}
\end{bmatrix}
\in \mathbb{R}^{n\times q},
\qquad z_{ij} \sim \text{i.i.d. } N(0,1).
$$

If we stack its columns into one long vector:

$$
\operatorname{vec}(Z) \sim N(0,\, I_{nq}).
$$

So $Z$ is just a “matrix-shaped” standard normal.

**Step 4️⃣. Introduce row and column correlations**

We now want a new matrix $X$ that is **Gaussian**, but has correlations both across rows and across columns.

We construct it as:

$$
X = M + A\,Z\,B^\top,
$$

where:

- $M \in \mathbb{R}^{n\times q}$ is the mean matrix;  
- $A \in \mathbb{R}^{n\times n}$ is a square matrix controlling row correlations;  
- $B \in \mathbb{R}^{q\times q}$ is a square matrix controlling column correlations;  
- $\Sigma = A A^\top$ (row covariance);  
- $\Psi = B B^\top$ (column covariance).

Thus:
- $A$ injects correlation between **rows** (vertical direction),
- $B$ injects correlation between **columns** (horizontal direction).

**Step 5️⃣. Convert to vectorized form**

We use the important Kronecker–vec identity:

$$
\boxed{\operatorname{vec}(A Z B^\top) = (B \otimes A)\,\operatorname{vec}(Z)}.
$$

Therefore:

$$
\operatorname{vec}(X)
= \operatorname{vec}(M) + (B\otimes A)\operatorname{vec}(Z).
$$

**Step 6️⃣. Find the distribution of $\operatorname{vec}(X)$**

Since $\operatorname{vec}(Z)\sim N(0, I_{nq})$,
a linear transformation preserves normality:
$$
\operatorname{vec}(X)
\sim
N\!\big(
\operatorname{vec}(M),\;
(B\otimes A)\,I_{nq}\,(B\otimes A)^\top
\big).
$$

Simplify the covariance using Kronecker product rules:

$$
(B\otimes A)(B\otimes A)^\top
= (B\otimes A)(B^\top\otimes A^\top)
= (B B^\top)\otimes(A A^\top)
= \Psi\otimes\Sigma.
$$

Hence:

$$
\boxed{
\operatorname{vec}(X)\sim N\!\big(\operatorname{vec}(M),\,\Psi\otimes\Sigma\big)
}.
$$

**Step 7️⃣. Arrive at the Matrix Normal definition**

By definition:

$$
\boxed{
X \sim MN_{n\times q}(M,\,\Sigma,\,\Psi)
\;\Longleftrightarrow\;
\operatorname{vec}(X)\sim N(\operatorname{vec}(M),\,\Psi\otimes\Sigma).
}
$$

**Step 8️⃣. Geometric and statistical intuition**

| Direction           | Transformation       | Covariance induced    | Matrix involved    |
| ------------------- | -------------------- | --------------------- | ------------------ |
| Row (vertical)      | Multiply by $A$      | $\Sigma = A A^\top$   | Row covariance     |
| Column (horizontal) | Multiply by $B^\top$ | $\Psi = B B^\top$     | Column covariance  |
| Combined effect     | Kronecker product    | $\Psi \otimes \Sigma$ | Overall covariance |

Intuitively:
- $A$ shapes dependencies across rows,  
- $B$ shapes dependencies across columns,  
- combining them gives a separable covariance structure $\Psi \otimes \Sigma$.

**Special Case: Independent Entries**

When  
$$
X \sim MN(M, I_n, \sigma^2 I_q),
$$
we have  
$$
\mathrm{Cov}(\mathrm{vec}(X)) = \Psi \otimes \Sigma = (\sigma^2 I_q) \otimes I_n = \sigma^2 I_{nq}.
$$

Thus:
- Every element $X_{ij}$ is **independent** of every other element.
- Each element follows  
  $$
  X_{ij} \sim N(\mu_{ij}, \sigma^2)
  $$
- Covariance between different elements is zero:  
  $$
  \mathrm{Cov}(X_{ij}, X_{kl}) =
  \begin{cases}
  \sigma^2, & (i,j) = (k,l) \\
  0, & \text{otherwise.}
  \end{cases}
  $$

## Basic Topics

### Point Estimation

Point estimation is using sample data to provide a single best guess or estimate of a population parameter. It goal is to produce a statistic that approximates an unknown parameter based on observed data.

Key Concepts in Point Estimation: **Parameter**, **Estimator**, **Estimate**.

Note: in addition to **point estimation**, there is another important approach known as **interval estimation**. 

### Generalized Linear Models

#### Score Function

**Expectation of the Score Function: Proofs, Regularity Conditions, and Exceptions**

> Provide the **initial proofs** (continuous and discrete), explain the **regularity conditions**, and discuss **piecewise, jump, and irregular** cases.  
>
> Conclude with why exponential families and GLMs are usually *regular models* satisfying these conditions.

**1️⃣ Definition and Main Result**

- For a single observation with PDF or PMF $f(y;\theta)$  
- Log-likelihood: $\ell(\theta) = \log f(Y;\theta)$  
- Score function: $u(\theta) = \partial_\theta \ell(\theta) = \partial_\theta \log f(Y;\theta)$

**Result (under regularity conditions):**

$$
\mathbb{E}_\theta[u(\theta)] = 0.
$$

**2️⃣ Initial Proofs**

**2.1 Continuous case (parameter-independent support)**

Let $Y \sim f(y;\theta)$ and $\int f(y;\theta) dy = 1$. Then

$$
\begin{aligned}
\mathbb{E}_\theta[u(\theta)]
&= \int \frac{\partial}{\partial \theta} \log f(y;\theta) \, f(y;\theta) \, dy \\[6pt]
&= \int \frac{\partial_\theta f(y;\theta)}{f(y;\theta)} \, f(y;\theta) \, dy \\[6pt]
&= \int \frac{\partial f(y;\theta)}{\partial \theta} \, dy.
\end{aligned}
$$

Under regularity (interchanging derivative and integral):

$$
\int \partial_\theta f(y;\theta) \, dy
= \partial_\theta \int f(y;\theta)\,dy
= \partial_\theta 1 = 0.
$$

Thus $\mathbb{E}_\theta[u(\theta)] = 0$.

**2.2 Discrete case (parameter-independent support)**

If $Y$ takes values in a fixed set $\mathcal{Y}$, similarly we have:

$$
\mathbb{E}_\theta[u(\theta)]
= \sum_{y \in \mathcal{Y}} \partial_\theta \log f(y;\theta)\,f(y;\theta)
= \sum_{y \in \mathcal{Y}} \partial_\theta f(y;\theta)
= \partial_\theta \sum_{y \in \mathcal{Y}} f(y;\theta)
= \partial_\theta 1 = 0.
$$

**3️⃣ Regularity Conditions**

The key step above is exchanging differentiation and integration/summation. This requires the following **regularity conditions** (sufficient, not necessary):

1. **Differentiability:** $f(y;\theta)$ is differentiable in $\theta$, and $\partial_\theta f(y;\theta)$ exists and is integrable.
   
2. **Parameter-independent support:** The domain of integration or summation does not depend on $\theta$, or any boundary terms vanish.
   
3. **Interchangeability:** A dominating function exists so that differentiation and integration can be interchanged (via dominated convergence or Leibniz’s rule).
   
4. **Normalization:** $\int f(y;\theta)\,dy = 1$ for all $\theta$.

Under these, $E_\theta[u(\theta)] = 0$ holds.

**4️⃣ Piecewise / Jump / Moving-Support Cases**

**4.1 Piecewise smooth density with fixed jump points**

Suppose $f(y;\theta)$ is piecewise smooth in $y$, with finitely many fixed jump points $c_1, c_2, \dots$ (independent of $\theta$).

Then the integral can be split:

$$
\int \partial_\theta f(y;\theta)\,dy
= \sum_k \int_{c_{k-1}}^{c_k} \partial_\theta f(y;\theta)\,dy
= \partial_\theta \sum_k \int_{c_{k-1}}^{c_k} f(y;\theta)\,dy
= \partial_\theta 1 = 0.
$$

✅ The proof must be adjusted to a *piecewise integration*, but the result **still holds** since the jump locations are fixed.

**4.2 Jump points or boundaries moving with θ**

If boundaries $a(\theta), b(\theta)$ or jump locations $c_k(\theta)$ depend on θ:

$$
\partial_\theta \!\int_{a(\theta)}^{b(\theta)} f(y;\theta)\,dy
= \int_{a(\theta)}^{b(\theta)} \partial_\theta f(y;\theta)\,dy
+ f(b(\theta);\theta)b'(\theta)
- f(a(\theta);\theta)a'(\theta)
+ \sum_k [f(c_k^-;\theta) - f(c_k^+;\theta)]\,c_k'(\theta).
$$

Since the left-hand side is always $0$ (normalization),

$$
\int \partial_\theta f(y;\theta)\,dy
= -\big[\text{boundary terms} + \text{jump terms}\big].
$$

Therefore, unless those extra terms cancel exactly,  

$$
\mathbb{E}_\theta[u(\theta)] = \int \partial_\theta f(y;\theta)\,dy \neq 0.
$$

**5️⃣ Examples and Counterexamples**

**✅ Special case (still holds by cancellation):**

Uniform$(0,\theta)$: $f(y;\theta) = \tfrac{1}{\theta} I(0 \le y \le \theta)$.

$$
\int_0^\theta \partial_\theta f\,dy = -\frac{1}{\theta},
\quad f(\theta;\theta)b'(\theta)=\frac{1}{\theta},
$$

which cancel, giving $E[u(\theta)] = 0$. This is a *nonregular model*, but the equality holds *by coincidence*.

**❌ Counterexample (fails):**

Shifted exponential:

$$
f(y;\theta) = I\{y>\theta\}\,e^{-(y-\theta)}, \quad y \in (\theta,\infty).
$$

Then

$$
u(\theta) = \partial_\theta \log f(y;\theta)
= 1,
\quad \Rightarrow \quad \mathbb{E}_\theta[u(\theta)] = 1 \ne 0.
$$

The support depends on θ, and boundary terms do **not** cancel. This is a classic *nonregular* example.



## Research Topics

### Conformal Prediction

Conformal prediction is a popular method for measuring prediction uncertainty. It is a non-parametric method for constructing prediction intervals that conform to the observed data, assuming exchangeability of data points. It provides a coverage guarantee, ensuring that the intervals cover the true outcomes with a specified probability (coverage level) over multiple iterations. The method is adaptive to the data, making minimal distributional assumptions, and is flexible in incorporating different conformal scores (measures of the discrepancy or distance between the observed and predicted responses). Conformal prediction yields statistically valid intervals that maintain the desired coverage probability without relying on distributional assumptions.

Conformal prediction can be adapted to incorporate a particular dataset or prediction task by customizing its components, such as the predictive model (e.g., deep neural networks, random forests, and SVM), scoring function, or algorithmic details, to better capture the data's characteristics.

The method can be sensitive to the choice of conformal score function.

## Other Math Knowledge

Here is notes of some knowledge taken when learning statistics.

### Fourier Transform and Sine Functions

#### 正交性的结构来源（乘积→频率分离）

正弦/余弦之所以能形成“正交基”，不仅是因为积分为零，更深层原因是它们具有良好的代数结构：

利用“积化和差公式”：
$$
\sin a \sin b = \frac{1}{2}[\cos(a-b) - \cos(a+b)]
$$

或用复指数形式：
$$
e^{i\omega_1 t} \cdot e^{-i\omega_2 t}
= e^{i(\omega_1-\omega_2)t}
$$

可以看到：

> 两个频率相乘 → 转化为“频率差”和“频率和”

因此在积分时：

- 若 $\omega_1 \ne \omega_2$ → 剩下的是非零频率振荡 → 平均抵消  
- 若 $\omega_1 = \omega_2$ → 变为常数 → 不会抵消  

这就是“正交性”的结构来源，而不仅仅是巧合。

---

#### 复指数与圆周运动（Euler 结构）

复指数函数：
$$
e^{i\omega t} = \cos(\omega t) + i\sin(\omega t)
$$

可以理解为复平面上的匀速圆周运动：

- 实部 → cos（横坐标）
- 虚部 → sin（纵坐标）
- $\omega$ → 角速度

因此：

> 正弦波本质上是“圆周运动在某一轴上的投影”

这也是为什么频率分析本质上等价于分析不同“旋转速度”的分量。

---

#### 傅立叶变换的本质（频率匹配 / 抵消机制）

傅立叶变换：
$$
X(\omega) = \int_{-\infty}^{\infty} x(t)e^{-i\omega t}dt
$$

可以理解为：

> 用 $e^{-i\omega t}$ 去“试探”信号中是否存在频率 $\omega$

如果信号中有：
$$
x(t) = e^{i\omega_0 t}
$$

那么：

$$
e^{i\omega_0 t} \cdot e^{-i\omega t}
= e^{i(\omega_0-\omega)t}
$$

- 当 $\omega = \omega_0$ → 变为常数 → 积分累积（非零）  
- 当 $\omega \ne \omega_0$ → 振荡 → 抵消（为0）

这就是“频率筛选”的本质。

---

#### 实信号与共轭频率（±ω 对称）

对于实信号：

$$
x(t) \in \mathbb{R}
$$

其频谱满足：

$$
X(-\omega) = X^*(\omega)
$$

即：

> 每个正频率都对应一个负频率（复共轭）

因此：

- 一个 cos 波 = 两个方向相反的复指数叠加  
- 傅立叶变换实际上是在分解这些“旋转分量”

---

#### 逆变换（频率重构时间）

傅立叶逆变换：

$$
x(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} X(\omega)e^{i\omega t}d\omega
$$

可以理解为：

> 把所有频率分量重新叠加回时间信号

- 正变换：分解（analysis）
- 逆变换：重构（synthesis）

**关于 $2\pi$ 的来源：**

$\omega$（角频率）与 $f$（普通频率）关系为：

$$
\omega = 2\pi f
$$

因此：

- 使用 $\omega$ → 公式里会出现 $\frac{1}{2\pi}$
- 使用 $f$ → 可以把 $2\pi$ 分散到指数中

这是约定问题，不影响本质。

---

#### 卷积与频域相乘 (Convolution and Frequency Domain Multiplication)

在时域中，**卷积** (Convolution) 是将一个信号在另一个信号的每一个位置上进行加权叠加；而在频域中，这对应于两个分量的直接**相乘** (Multiplication)。这使得处理随机变量之和的**特征函数** (Characteristic Function) 时，复杂的卷积运算简化为了简单的代数乘法。

---

#### 卷积与乘法：时域和频域的对偶关系

Fourier transform 最核心的思想之一：

> 时域中的“局部传播 / 叠加”
>
> 会在频域中变成“频率之间的代数操作”。

其中最重要的两组对应关系：

| 时域                  | 频域                  | 直观意义            |
| --------------------- | --------------------- | ------------------- |
| 卷积 (Convolution)    | 乘法 (Multiplication) | 频率筛选 / 滤波     |
| 乘法 (Multiplication) | 卷积 (Convolution)    | 频率混合 / 频谱平移 |

---

**一、时域卷积 ↔ 频域相乘**

**1. 时域中的卷积**

卷积定义：

$$
(f*g)(t)
=
\int f(\tau)g(t-\tau)d\tau
$$

它的本质是：

> 用一个函数 $g$ 在另一个函数 $f$ 上不断滑动，
>
> 每个位置做加权叠加。

也可以理解为：

- 系统对历史输入的累积响应
- 用模板扫描信号
- 邻域信息融合

**2. 卷积最重要的物理意义：系统响应**

若：

- $f(t)$：输入信号
- $g(t)$：系统的 impulse response（冲激响应）

则：

$$
(f*g)(t)
$$

表示：

> 信号经过系统后的输出。

例如：

- 图像模糊
- RC 电路
- 麦克风回声
- 神经元膜电位积分
- Gaussian smoothing

本质都是卷积。

**3. 为什么卷积会变成频域乘法？**

关键：

Fourier basis：

$$
e^{i\omega t}
$$

是卷积算子的特征函数。

假设输入是单个频率：

$$
f(t)=e^{i\omega t}
$$

则：

$$
g * e^{i\omega t}
$$

会发现：

系统不会改变它的频率，

只会：

- 放大 / 缩小
- 改变相位

即：

$$
g * e^{i\omega t}
=
G(\omega)e^{i\omega t}
$$

这里：

$$
G(\omega)
$$

就是系统对频率 $\omega$ 的响应。

因此：

> 对每个频率，
>
> 卷积系统只是“乘一个数”。

于是：

$$
\mathcal F(f*g)
=
F(\omega)G(\omega)
$$

---

**二、卷积最直观的理解：滤波**

这是最重要的工程直觉。

**低通滤波器例子**

假设：

$$
G(\omega)
=
\begin{cases}
1,& |\omega|<\omega_c \\
0,& \text{otherwise}
\end{cases}
$$

意思：

- 低频保留
- 高频删除

则：

$$
F(\omega)G(\omega)
$$

表示：

- 保留低频部分
- 高频直接乘成 0

回到时域：

结果：

- 信号变平滑
- 边缘变模糊
- 高频震荡消失

因此：

> 时域卷积
>
> 本质就是：
>
> 频域筛频率（滤波）。

---

**三、时域乘法 ↔ 频域卷积**

现在反过来。

**时域中的乘法**

时域乘法：

$$
h(t)=f(t)g(t)
$$

本质是：

> 一个信号被另一个信号“调制” (modulation)。

例如：

- AM 调制
- windowing
- beating（拍频）

都属于时域乘法。

---

**四、为什么时域乘法对应频域卷积？**

最直观的方法：

看单个频率相乘。

**例子：两个余弦波相乘**

设：

$$
f(t)=\cos(\omega_1 t)
$$

$$
g(t)=\cos(\omega_2 t)
$$

则：

利用积化和差公式：

$$
\cos(\omega_1 t)\cos(\omega_2 t)
=
\frac12
\left[
\cos((\omega_1-\omega_2)t)
+
\cos((\omega_1+\omega_2)t)
\right]
$$

这个公式极其重要。

它说明：

> 时域中两个频率相乘，
>
> 会生成：
>
> - 频率差
> - 频率和

即：

$$
\omega_1,\omega_2
\rightarrow
\omega_1-\omega_2,\ \omega_1+\omega_2
$$

这意味着：

> 频率之间发生了“混合”。

也就是说：

- 原来的频率不再独立
- 它们会彼此产生新的频率成分

---

**五、频域中的“卷积”是什么？**

卷积本质：

> 一个频谱去“复制并平移”另一个频谱。

例如：

若：

$$
g(t)=e^{i\omega_0 t}
$$

则：

$$
f(t)e^{i\omega_0 t}
$$

Fourier transform：

$$
F(\omega-\omega_0)
$$

即：

> 整个频谱整体平移。

因此：

时域乘法

=
频域中的频谱搬运 / 扩散 / 平移。

更一般地：

$$
\mathcal F(fg)
=
F*G
$$

表示：

\(G\) 中每个频率，

都会：

- 复制
- 平移
- 加权

整个 \(F\)。

---

**六、最核心直觉**

**1. 时域卷积 ↔ 频域乘法**

核心：

> 各个频率彼此独立处理。

每个频率：

$$
F(\omega)
\rightarrow
F(\omega)G(\omega)
$$

因此：

- 本质是“频率筛选”
- 即滤波 (filtering)

**2. 时域乘法 ↔ 频域卷积**

核心：

> 不同频率彼此混合。

一个频率：

会把另一个频谱：

- 平移
- 复制
- 扩散

因此：

- 本质是“频率混频”
- 即 modulation（调制）

---

**七、最重要总结**

| 时域操作 | 频域操作 | 本质直觉        |
| -------- | -------- | --------------- |
| 加法     | 加法     | 信号叠加        |
| 卷积     | 乘法     | 频率筛选 / 滤波 |
| 乘法     | 卷积     | 频率混合 / 调制 |
| 平移     | 相位变化 | 改变相位        |
| 调制     | 频谱平移 | 搬运频率        |

---

**八、最终直观理解**

可以这样记忆：

**时域卷积**

表示：

> 一个系统如何处理不同频率。

因此：

频域里变成：

> 每个频率单独乘倍率。

即：

> 滤波。

**时域乘法**

表示：

> 两个振荡彼此干涉。

因此：

频域里变成：

> 不同频率互相混合。

即：

> 频谱卷积 / 频谱搬运。

---

**九、更深层本质（重要）**

Fourier transform 的真正力量：

它把：

> 卷积算子**对角化**了。

因为：

$$
e^{i\omega t}
$$

是**卷积算子的特征函数**。

因此：

复杂卷积：

$$
f*g
$$

在频域里，

变成：

$$
F(\omega)G(\omega)
$$

即：

> 无穷维积分运算
>
> 变成
>
> 点对点代数乘法。

这也是：

- 信号处理
- PDE
- Quantum mechanics
- Probability
- Deep learning
- Green's function

中 Fourier transform 如此重要的根本原因。

---

**十、概率论中的对应：随机变量之和与特征函数**

在概率论里，

Fourier transform 的一个最重要应用是：

> 随机变量“相加”
>
> 会对应概率密度之间的卷积。

**1. 随机变量之和对应概率密度卷积**

设：

$$
Z=X+Y
$$

且：

- $X,Y$ 独立
- 概率密度分别为：$f_X,f_Y$

则：

$Z$ 的概率密度为：

$$
f_Z(z)
=
(f_X * f_Y)(z)
=
\int
f_X(x)f_Y(z-x)\,dx
$$

这表示：

> 为了得到 $Z=z$，
>
> 需要枚举：
>
> 所有可能的
>
> $X=x,\ Y=z-x$
>
> 的组合。

因此：

> “随机变量相加”
>
> 在概率密度层面，
>
> 本质就是卷积。

**2. 特征函数 (Characteristic Function)**

概率论里通常不用标准 Fourier transform 的负号 convention，

而定义：

$$
\phi_X(t)
=
\mathbb E[e^{itX}]
$$

称为：

随机变量 $X$ 的特征函数。

它本质上：

就是概率密度的 Fourier transform。

（只是符号 convention 略有不同。）

**3. 为什么特征函数特别重要？**

因为：

随机变量求和：

$$
Z=X+Y
$$

在概率密度层面是卷积：

$$
f_Z=f_X*f_Y
$$

但在特征函数层面：

卷积会变成乘法：

$$
\phi_Z(t)
=
\phi_X(t)\phi_Y(t)
$$

即：

$$
\phi_{X+Y}(t)
=
\phi_X(t)\phi_Y(t)
\quad
(X,Y\ \text{independent})
$$

**4. 直观理解**

因此：

> “随机变量相加”
>
> 在时域 / 概率密度里，
>
> 是复杂的卷积。

但：

> 在频域 / 特征函数里，
>
> 变成简单的代数乘法。

这也是：

- 中心极限定理
- Lévy process
- 稳定分布
- 随机过程
- Gaussian 分布封闭性

等大量概率论结果背后的核心原因。

**5. 最核心总结**

| 概率论对象      | Fourier / 频域对应 |
| --------------- | ------------------ |
| 概率密度 $f(x)$ | 特征函数 $\phi(t)$ |
| 随机变量求和    | 概率密度卷积       |
| 独立性          | 特征函数相乘       |

因此：

> Fourier transform
>
> 把“随机变量相加”
>
> 转化成了：
>
> “特征函数相乘”。

---

#### LTI 系统与正弦波特征函数 (LTI Systems and Sinusoidal Eigenfunctions)

**线性时不变系统** (LTI System) 对**正弦波** (Sinusoidal Wave) 的处理仅限于改变其**振幅** (Amplitude) 和**相位** (Phase)，而不改变频率，因此正弦波是 LTI 的**特征函数** (Eigenfunction)。不同频率的**线性组合** (Linear Combination) 信号通过系统时，由于系统对各频率的**频率响应** (Frequency Response) 不同，合成形状会改变，因此整体不再是特征函数。

---

#### 快速傅里叶变换 (FFT) 原理

**快速傅里叶变换** (FFT) 是**离散傅里叶变换** (DFT) 的高效算法实现。它利用正弦基函数的**对称性** (Symmetry) 和**周期性** (Periodicity)，通过分治策略将计算复杂度从 $$O(N^2)$$降低到$$O(N \log N)$$。它在理论上与 DFT 等价，仅存在微小的计算机**舍入误差** (Rounding Error)。

---

#### 正弦波的完备性与正交性 (Completeness and Orthogonality)

* **完备性 (Completeness)：**
    正弦和余弦函数在平方可积函数空间（$L^2$ 空间）中构成一组完备基（complete basis）。这意味着：任意有限能量信号都可以表示为这些正弦波的叠加（傅立叶展开）。
    
    注：Stone–Weierstrass 定理可以说明连续函数的逼近能力，但傅立叶分析中更常用的是 Hilbert 空间中的正交基理论。
    
* **吉布斯现象 (Gibbs Phenomenon)：**
    当用有限个正弦波逼近**具有跳变（不连续点）的信号**（如方波）时，在不连续点附近会产生振荡，并出现约 9% 的固定过冲（overshoot）。
    
    需要注意：
    
    1. 该过冲幅值不会随着项数增加而消失，而是逐渐趋近一个固定值（约 0.08949，即约 9%）。
    
    2. 随着正弦项数增加：
       - 过冲的**高度基本不变**
       - 振荡的**宽度逐渐缩小（局部化）**
    
    3. 在极限（无穷项）情况下：
       - 在所有连续点处，傅立叶级数收敛到原函数
       - 在跳跃点处，收敛到左右极限的平均值
       - 过冲仍然存在，但被限制在一个趋于零宽度的邻域内
    
    因此，Gibbs 现象不会被“消除”，只能在极限下被压缩到局部区域，从整体上实现对原函数的逼近。这本质是：**用连续函数逼近不连续函数，必然会产生“振荡补偿”。**
    
* **谱泄漏 (Spectral Leakage)：**
    实际信号总是在有限时间窗口内观测，相当于将信号乘以一个“矩形窗”。这会导致频域中的卷积效应，使原本集中在单一频率的能量扩散到邻近频率（泄漏）。
    
    注：本质原因是“时域截断 ↔ 频域扩展”。
    
* **窗函数 (Windowing)：**
    为减少谱泄漏，可以使用平滑窗函数（如 Hamming Window 或 Hann Window）替代矩形窗。它们通过减弱边界的不连续性来降低频域旁瓣（leakage），但代价是主瓣变宽（频率分辨率下降）。
    
* **正交性的深层理解 (Orthogonality)：**
    对于不同频率的正弦波，我们常看到类似说法：
    $$
    \int_{-\infty}^{\infty} \sin(2\pi f_1 t)\sin(2\pi f_2 t)\,dt = 0
\quad (f_1 \ne f_2)
    $$
    但严格来说，这个式子不能按普通积分直接理解。在无穷区间上，这类振荡积分通常并不作为普通数值积分收敛。更准确的理解需要分两层：

    1. **有限区间上的正交性**
    
    在有限区间内，如果区间长度刚好包含整数个周期，不同频率的正弦波会出现严格抵消。例如在傅立叶级数中：
    
    $$
    \int_{-T}^{T} \sin\left(\frac{n\pi t}{T}\right)
\sin\left(\frac{m\pi t}{T}\right)dt = 0
    \quad (n \ne m)
    $$
    
    这里的正交性是普通积分意义下成立的，因为区间有限，而且频率与区间长度匹配。
    
    2. **无穷区间上的情况**
    
    对于连续频率的傅立叶变换，常用复指数表示：
    
    $$
    e^{i\omega_1 t}e^{-i\omega_2 t}
    =
    e^{i(\omega_1-\omega_2)t}
    $$
若记：
    $$
    \Delta\omega = \omega_1-\omega_2
    $$
    
    则有限区间积分为（<span style="color:red">下面的公式很重要</span>）：
    
    $$
    \int_{-T}^{T} e^{i\Delta\omega t}\,dt
    =
    \left[ \frac{e^{i\Delta\omega t}}{i\Delta\omega} \right]_{-T}^{T}
    =
    \frac{e^{i\Delta\omega T} - e^{-i\Delta\omega T}}{i\Delta\omega}
    =
    \frac{2\sin(\Delta\omega T)}{\Delta\omega}
    \quad (\Delta\omega \ne 0)
    $$
    
    > 注：这就是著名的**Sinc 函数（sinc function）**的形式。其标准定义为：
    >
    > **数学形式（非归一化）**：$\text{sinc}(x) = \frac{\sin(x)}{x}$，零点位于 $x = \pm k\pi$（$k$ 为正整数）；
    >
    > **工程形式（归一化）**：$\text{sinc}(x) = \frac{\sin(\pi x)}{\pi x}$，零点位于 $x = \pm k$（$k$ 为正整数）。
    
    关于sinc函数，参见[Sinc函数在傅里叶变换中的应用](#Sinc函数在傅里叶变换中的应用)。
    
    当 $T \to \infty$ 时，这个结果会持续振荡，并不会收敛到某个普通数值。所以不能简单说：
    $$
    \int_{-\infty}^{\infty} e^{i\Delta\omega t}dt = 0
    $$
    
    这是普通积分意义下不严谨的写法。
    
    3. **分布意义下的写法**
    
    在傅立叶分析中，更严格的写法是（<span style="color:red">下面的公式很重要</span>）：
    
    $$
    \int_{-\infty}^{\infty} e^{i(\omega-\omega_0)t}dt
    =
    2\pi\delta(\omega-\omega_0)
    $$
    
    这里的等号不是普通函数值相等，而是**分布意义下相等**。和sinc函数的积分有关，参见[Sinc函数在傅里叶变换中的应用](#Sinc函数在傅里叶变换中的应用)。关于分布意义，参见[Distribution Theory（分布理论 / 广义函数理论）](#Distribution Theory（分布理论 / 广义函数理论）)。
    
    也就是说，这个表达式本身不是一个普通函数，而是一个“作用规则”：当它与一个合适的测试函数 $g(\omega)$ 相乘并积分时，有：
    
    $$
    \int_{-\infty}^{\infty}
    \left[
    \int_{-\infty}^{\infty} e^{i(\omega-\omega_0)t}dt
    \right]
    g(\omega)d\omega
    =
    2\pi g(\omega_0)
    $$
    
    而 Dirac delta 函数也满足：
    
    $$
    \int_{-\infty}^{\infty}
    2\pi\delta(\omega-\omega_0)g(\omega)d\omega
    =
    2\pi g(\omega_0)
    $$
    
    因此，两者对所有合适的测试函数作用结果相同，所以说它们在分布意义下相等。
    
    这里的测试函数不能是整个无穷区间上的常数 $1$，而通常要求平滑并在无穷远处衰减，或具有有限支撑。否则积分本身可能没有定义。
    
    4. **“频率不同为零”的真正含义**
    
    由于
    
    $$
    \delta(\omega-\omega_0)
    $$
    
    只在 $\omega=\omega_0$ 处有贡献，所以当频率不匹配时：
    
    $$
    \omega \ne \omega_0
    $$
    
    对应的贡献为零。
    
    因此，“不同频率正交”更准确地说是：
    
    > 不同频率的分量在傅立叶分解中不会互相贡献。频率匹配时由 Dirac delta 提取出对应分量；频率不匹配时贡献为零。
    
    所以，常见写法
    
    $$
    \int_{-\infty}^{\infty} e^{i(\omega_1-\omega_2)t}dt = 0
    \quad (\omega_1 \ne \omega_2)
    $$
    应理解为一种傅立叶分析中的简写。它不是说这个无穷振荡积分作为普通积分真的收敛为零，而是说：在分布意义下，它只在 $\omega_1=\omega_2$ 时有贡献；当$\omega_1\ne\omega_2$ 时没有贡献。
    
* **傅立叶级数与傅立叶变换的关系 (Series vs Transform)：**

    傅立叶级数与傅立叶变换描述的是同一类“频率分解”思想，但适用于不同情形：

    1. **傅立叶级数（有限区间 / 周期信号）**

    对周期信号，在一个周期内可以进行**严格积分计算**：
    $$
    C_n = \frac{1}{T}\int_0^T x(t)e^{-i n\omega_0 t}\,dt
    $$
    
    其中频率为离散值：
    
    $$
    \omega = n\omega_0
    $$
    
    在这种情况下：
    
    - 正交性是**严格计算结果**
    - 不同频率项的积分确实等于 0（在整数周期内）
    - 没有使用分布或极限
    
    👉 本质：**离散频率 + 有限区间上的精确积分**
    
    2. **傅立叶变换（无穷区间 / 非周期信号）**
    
    对非周期信号，需要在整个实数轴上积分：
    
    $$
    X(\omega) = \int_{-\infty}^{\infty} x(t)e^{-i\omega t}dt
    $$
    
    此时：
    
    - 频率是连续变量
    - 振荡积分通常不收敛
    - 正交性不再是普通积分结果
    
    因此需要用分布来描述：
    
    $$
    \int_{-\infty}^{\infty} e^{i(\omega_1-\omega_2)t}dt
    =
    2\pi\delta(\omega_1-\omega_2)
    $$
    
    👉 本质：**连续频率 + 分布意义**
    
    3. **两者之间的联系**
    
    傅立叶变换可以看作傅立叶级数在周期趋于无穷时的极限形式：
    
    - 周期 $T \to \infty$
    - 频率间隔 $\Delta \omega \to 0$
    - 离散谱 → 连续谱
    
    👉 可以理解为：
    
    > 傅立叶级数：离散频率上的精确分解 
    > 
    > 傅立叶变换：连续频率上的极限分解（通过分布定义）
    
    4. **正交性的统一理解**
    
    - 在傅立叶级数中：
      不同频率的正交性是**严格积分结果**
    
    - 在傅立叶变换中：
      “正交性”体现为：
      $$
      \delta(\omega_1-\omega_2)
      $$
    
    👉 即：
    
    > 不是直接算出 0，而是通过分布表达“只有频率匹配才有贡献”



#### Sinc函数在傅里叶变换中的应用

**1. 有限时间窗的傅里叶变换**

考虑一个长度为 $2T$ 的时间窗，对应的傅里叶变换为：

$$
F_T(\omega) = \int_{-T}^{T} e^{i \Delta \omega t} \, dt
$$

计算可得：

$$
F_T(\omega) = \frac{2 \sin(\Delta \omega T)}{\Delta \omega}
$$

这就是著名的 **Sinc 函数（sinc function）** 的形式。

---

**2. Sinc 函数的一个关键性质：面积不变**

一个非常重要且“反直觉”的性质是：

> 无论 $T$ 多大，该函数在整个频率轴上的积分（面积）始终是一个常数。

即：

$$
\int_{-\infty}^{\infty} \frac{2 \sin(\Delta \omega T)}{\Delta \omega} \, d(\Delta \omega) = 2\pi
$$

> 这里用到著名的 Dirichlet integral：
>
> $$
> \int_0^\infty \frac{\sin u}{u}\,du = \frac{\pi}{2}
> $$
>
> 该积分虽然不是绝对收敛的，但由于振荡的正负抵消而条件收敛，是 Fourier analysis 与 distribution theory 中的重要经典结果。
>
> 经典证明技巧：给积分加入指数阻尼因子 $e^{-ax}$，构造辅助函数$I(a)=\int_0^\infty e^{-ax}\frac{\sin x}{x}dx$，然后对参数 $a$ 求导，将困难积分转化为容易计算的 Laplace 积分，最后令 $a\to0^+$ 即可得到结果。

**直观理解**

- 当 $T$ 增大时：
  - 函数在 $\omega=0$ 附近越来越“尖”
  - 振荡越来越快
- 但：
  - **总面积始终保持为 $2\pi$**

这是一种典型的“高度集中但面积守恒”的行为。

---

**3. 极限 $T \to \infty$：经典函数的困境**

当 $T \to \infty$ 时：

- 函数在 $\omega = 0$ 附近变得“无限高”
- 在其他地方持续振荡
- 但总面积仍为 $2\pi$

于是我们得到一个“怪物”：

> 在 0 点趋于无穷，在其他地方剧烈振荡，但整体积分有限

这在**经典函数意义下是不合法的函数**。

---

**4. 分布理论（Distribution Theory）的引入**

为了解决这个问题，数学家 **Laurent Schwartz** 提出了：

> **分布理论（广义函数理论）**

---

**5. 分布的核心思想**

核心转变是：

> 不再孤立地讨论一个函数在某一点的取值，
> 而是研究它与“测试函数（test function）”作用后的整体表现。

具体来说：

- 取一个平滑函数 $\phi(\omega)$（测试函数）
- 关注的是：

$$
\int f(\omega)\,\phi(\omega)\,d\omega
$$

而不是 $f(\omega)$ 在某一点的值

---

**6. Dirac δ 的自然出现**

在这个框架下：

$$
\lim_{T \to \infty} \frac{2 \sin(\Delta \omega T)}{\Delta \omega}
$$

不再被看作普通函数，而被理解为：

$$
2\pi \, \delta(\Delta \omega)
$$

其中 $\delta(\cdot)$ 是 **Dirac delta 分布**。

---

**7. 直观总结（一句话版本）**

- 有限时间窗 → sinc
- 时间窗变大 → sinc 变尖
- 极限 → δ 分布
- 面积守恒 → $2\pi$

---

**8. 关键理解（非常重要）**

这个等价关系的真正含义是：

$$
\int \frac{2 \sin(\Delta \omega T)}{\Delta \omega} \, \phi(\omega)\, d\omega
\;\xrightarrow{T\to\infty}\;
2\pi \, \phi(0)
$$

而不是点值上的收敛。

---

#### Distribution Theory（分布理论 / 广义函数理论）

分布理论（distribution theory）的核心思想是：

> 一个对象最重要的，不是它在每一点的“函数值”，而是它对所有平滑测试函数（test functions）的整体作用。

因此，不再孤立地讨论 $f(x)$ 在某一点的取值，而是研究：

$\int f(x)\phi(x)\,dx$

对所有平滑函数 $\phi(x)$ 的作用结果。

这种思想的意义在于：

很多重要对象（例如 Dirac delta）根本无法作为普通函数存在。因为它表现为：

- 在一个点“无限高”
- 其它地方为 0
- 但整体面积仍有限

这在经典函数理论中是矛盾的。

于是，分布理论换了一个角度：

> 不直接研究对象本身，而是研究它对“平滑探针（测试函数）”的响应。

例如，Dirac delta 不再被理解为某个“无限高的函数”，而是被定义为：

$$
\int \delta(x)\phi(x)\,dx = \phi(0)
$$

即：

> $\delta(x)$ 的作用是“提取测试函数在 0 点的值”。

因此，分布理论本质上是一种：

> 从“点值观点”转向“整体作用观点”的数学思想。

它使得 Fourier transform、PDE、量子力学等领域中的许多“奇异对象”获得了严格数学意义。