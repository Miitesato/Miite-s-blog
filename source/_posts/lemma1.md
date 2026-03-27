---
title: 3.lemma1证明_(1)
date: 2026-03-28 02:57:00
tags:
  \ - ETIC-based cluster synchronization
---

**Lemma1**



去除随机扰动项后的脉冲系统如下：
$$
\begin{cases} 
\dot{w}(t)=dw(t)/dt = \mathcal{F}(t, w(t), w(t - \tau_0)) , \quad t \geq t_0, \quad t \neq t_k \\ 
w(t_k) = \mathcal{H}_k(z_k, w(z_k)), \quad k \in Z_+ \\ 
w(\varepsilon) = \zeta(\varepsilon), \quad \varepsilon \in [t_0 - \tau_0, t_0]
\end{cases}\
$$


- $ w(t) \in \mathbb{R}^{Nn} $：状态向量。
- $ \mathcal{F}, \mathcal{G} \in C([t_{k-1}, t_k) \times \mathbb{C}, \mathbb{R}^{Nn}) $：函数 $ \mathcal{F} $ 在区间 $[t_{k-1}, t_k)$ 与函数空间 $ \mathbb{C} $ 上连续。
- $ \mathbb{C} \in PC([t_0 - \tau_0, t_0], \mathbb{R}^{Nn}) $：$ \mathbb{C} $ 表示分段连续函数空间，定义域为 $[t_0 - \tau_0, t_0]$，值域为 $\mathbb{R}^{Nn}$。
- $ \mathcal{F}(t, 0) = \mathcal{G}(t, 0) = 0, \quad \forall t \geq t_0 $：系统在零状态下的平衡条件。
- $ \mathcal{H}_k \in C(\Omega \times \mathbb{R}^{Nn}, \mathbb{R}^{Nn}) $：脉冲函数 $ \mathcal{H}_k $ 在 $\Omega \times \mathbb{R}^{Nn}$ 上连续。
- $ \Omega $：脉冲激活时间的集合。
- $ \mathcal{H}_k(t_k, 0) = 0, \quad \forall k \in \mathbb{Z}_+ $：脉冲函数在零状态下的平衡条件。
- $ \zeta \in PC([t_0 - \tau_0, t_0], \mathbb{R}^{Nn}) $：初始函数，属于分段连续函数空间。
- 范数定义：$\|s\| = \sup\limits_{t_0 - \tau_0 \leq \varepsilon \leq t_0} |\zeta(\varepsilon)|$。



**前提条件：**

假设 $V(t, w(t)) \in v_0$，且存在正常数 $a$, $b$, $b \leq a$, $\tau_k$, $\gamma$, $\alpha_k$, $M$, $d_k$, $\sigma_1$, $\sigma_2$, ${\vartheta} $ 满足以下条件。

**1）**

$
\sigma_1 |w(t)|^{\vartheta} \leq V(t, w(t)) \leq \sigma_2 |w(t)|^{\vartheta}  \quad \forall (t, w(t)) \in [t_0 - \tau_0, +\infty) \times \mathbb{R}^{Nn}.
$

 **2)**

$
\Phi V(t, w(t)) \leq aV(t, w(t)) \quad \forall t \in [t_{k-1}, z_k) \text{ 当 } e^{\gamma \theta} V(t + \theta, w(t + \theta)) \leq e^{M} V(t, w(t)) \text{ 时},
$
$
\text{且 } \Phi V(t, w(t)) \leq bV(t, w(t)) \quad \forall t \in [z_k, t_k).
$

 **3)**

$
V(t_k) \leq e^{-(d_k + \gamma \tau_k)} V(z_k),
$
其中 $t_k = z_k + \tau_k$，$z_k$ 由事件脉冲触发条件（ETIC）定义如下：
$z_k = \inf\{t > t_{k-1} \mid \Gamma(t) \geq 0\}, \quad k \in \mathbb{Z}_+ \tag{8}$

> $z_k$​ 指的 **所有满足时间在上一次脉冲之后且触发条件成立的时间 t 的集合** 的下确界，即“满足时间在上一次脉冲之后且触发条件成立”的**第一次触发的时间**
>
> 即**第 k 次脉冲**发生在：从上一次脉冲之后，系统第一次满足触发条件的时刻
>
> 用下确界来定义是为了确保$z_k$一定能取到，

其中，

触发条件为：$\Gamma(t) = e^{\gamma(t-t_0)} V(t) - e^{\alpha_k} \left[ e^{\gamma(t_{k-1}-t_0)} V(t_{k-1}) \lor V_{t_0} \right],$
$V_{t_0} = \sup_{\epsilon \in [t_0-\tau_0, t_0]} V(\epsilon, \zeta(\epsilon)).$​



 **4)**

$
\alpha_k + (b + \gamma) \tau_k + \sum_{i=1}^l (\alpha_{k-i} - d_{k-i}) \leq M,
$
$
\lim_{k \to \infty} \sum_{i=1}^k \alpha_i + (b + \gamma) \tau_i \to \infty, \quad l \in I[1, k-1],
$
$
k \in \mathbb{Z}_+.
$



V(t) ：系统“能量”

Δ(t) = $e^{γt}$ V(t) ：放大后的能量

ETIC：
当 Δ(t) 增长到某个阈值 → 触发控制（脉冲）

目标：
让 Δ(t) 始终不会“无限增长”
⇒ V(t) 必然指数下降
⇒ w(t) → 0



**引理1证明：**

 假设 $ w(t) = w(t, t_0, \zeta) $ （初始时刻 $t_0$ 开始，以初始函数 $\zeta$ 作为历史，得到在任意 $t\ge t_0$ 时刻的状态$w(t)$）是系统 (7) 的一个解.

其初始条件为 $ w(\varepsilon) = \zeta(\varepsilon) $，$ t_0 - \tau_0 \leq \varepsilon \leq t_0 $。

首先，证明系统 (7) 的全局指数稳定性。

引入一个辅助函数并令 $ V(t) = V(t, w(t)) $ 

> 李雅普诺夫函数（能量函数）依赖于时间 t 和当前状态 w(t) ）

$$
\Delta(t) = 
\begin{cases} 
e^{\gamma(t-t_0)}V(t), & t \geq t_0 \\ 
V_{t_0}, & t_0 - \tau_0 \leq t \leq t_0 
\end{cases}
\tag{9}
$$

其中 $ \Delta_{t_0} = V_{t_0} =\sup_{\epsilon \in [t_0-\tau_0, t_0]} V(\epsilon, \zeta(\epsilon))$

>**对于辅助函数$\Delta(t)$​ 的理解：**
>
>$\gamma>0且t-t_0≥0$ $\Rightarrow$ $e^{\gamma(t-t_0)}\geq e^0=1$ ,即在 $t \geq t_0$时，把 $V(t)$ 放大了 $e^{\gamma(t-t_0)}$​ 倍，便于后续简化触发条件表达式
>
>定义初始初始区间$t_0 - \tau_0 \leq t \leq t_0 $ 能量函数值为**初始区间里能量的最大值**

基于 $ \Delta(t) $​，原触发条件

> $t=z_k$ 满足 $\Gamma(t) = e^{\gamma(t-t_0)} V(t) - e^{\alpha_k} \left[ e^{\gamma(t_{k-1}-t_0)} V(t_{k-1}) \lor V_{t_0} \right] \geq 0$ 

 可转化为：
$$
\Gamma(t) = \Delta(t) - e^{\alpha_k} \left[ \Delta(t_{k-1}) \lor V_{t_0} \right]
$$

>$\Gamma(t) = 当前能量 - 阈值$
>
>$触发条件：\Gamma(t) ≥0，即当前能量 ≥ 阈值$​
>
>阈值是“上个作用时刻的能量”与“历史最大能量”取最大
>
>$e^{\alpha_k}$ 的作用：增大阈值防止频繁触发

则：
$$
z_k = \inf\{t > t_{k-1} \mid \Delta(t) \geq e^{\alpha_k} \overline{\Delta}(t_{k-1})\}, \quad k \in Z_+ \tag{10}
$$

其中 $ \overline{\Delta}(t_k) = \Delta(t_k) \lor \Delta_{t_0} $。根据事件触发条件 (10)，有

$$
\Delta(z_k) = e^{\alpha_k} \overline{\Delta}(t_{k-1}), \tag{11}
$$

以及

$$
\Delta(t) \leq e^{\alpha_k} \overline{\Delta}(t_{k-1}), \quad t \in [t_{k-1}, z_k]. \tag{12}
$$



根据条件：

$\Phi V(t, w(t)) \leq aV(t, w(t)) \quad \forall t \in [t_{k-1}, z_k) \text{ 当 } e^{\gamma \theta} V(t + \theta, w(t + \theta)) \leq e^{M} V(t, w(t)) \text{ 时},$
$
\text{且 } \Phi V(t, w(t)) \leq  \quad \forall t \in [z_k, t_k).
$​



得到：

在连续演化区间 $t \in [z_k, t_k]$（脉冲触发后到作用前），有：

$D^+ \Delta(t) = \frac{d}{dt} \left[ e^{\gamma(t-t_0)} V(t) \right] = \gamma e^{\gamma(t-t_0)} V(t) + e^{\gamma(t-t_0)} \dot{V}(t) = (\gamma V(t) + \Phi V(t)) e^{\gamma(t-t_0)}$



即：
$$
D^+ \Delta(t) = (\gamma V(t) + \Phi V(t)) e^{\gamma (t-t_0)}
$$
$$
\leq(\gamma V(t) + bV(t)) e^{\gamma (t-t_0)}
$$

$$
\leq (b + \gamma) e^{\gamma (t-t_0)} V(t)
$$
$$
= (b + \gamma) \Delta(t), \quad t \in [z_k, t_k] \tag{13}
$$

且有：

$$
\Delta(t) \leq e^{(b+\gamma)(t-z_k)} \Delta(z_k)
$$
$$
= e^{\alpha_k + (b+\gamma)(t-z_k)} \overline{\Delta}(t_{k-1})
$$
$$
\leq e^{\alpha_k + (b+\gamma) \tau_k} \overline{\Delta}(t_{k-1}), \quad t \in [z_k, t_k]. \tag{14}
$$

由于 $(b+\gamma) \tau_k \geq 0$，结合 (12) 和 (14)，可得

$$
\Delta(t) \leq e^{\alpha_k + (b+\gamma) \tau_k} \overline{\Delta}(t_{k-1}), \quad t \in [t_{k-1}, t_k]. \tag{15}
$$

根据条件 (3)，我们有

$$
e^{\gamma (t_k - t_0)} V(t_k) \leq e^{\gamma (t_k - t_0)} e^{-(d_k + \gamma \tau_k)} V(z_k)
$$
$$
\leq e^{-d_k} e^{\gamma (z_k - t_0)} V(z_k) \tag{16}
$$



这意味着  

$$
\Delta(t_k) \leq e^{-d_k} \Delta(z_k) \tag{17}
$$

以及  

$$
\Delta(t) \leq e^{\alpha_k + (b+\gamma)\tau_k} \overline{\Delta}(t_{k-1})
$$

$$
\leq 
\begin{cases} 
e^{\alpha_k + (b+\gamma)\tau_k} \Delta(t_{k-1}), & \text{若 } \Delta(t_{k-1}) > \Delta_{t_0} \\ 
e^{\alpha_k + (b+\gamma)\tau_k} \Delta_{t_0}, & \text{若 } \Delta(t_{k-1}) \leq \Delta_{t_0}
\end{cases}
$$

$$
\leq 
\begin{cases} 
e^{\alpha_k - d_{k-1} + (b+\gamma)\tau_k} \Delta(z_{k-1}), & \text{若 } \Delta(t_{k-1}) > \Delta_{t_0}, \\ 
e^{\alpha_k + (b+\gamma)\tau_k} \Delta_{t_0}, & \text{若 } \Delta(t_{k-1}) \leq \Delta_{t_0}.
\end{cases}
$$

$$
\leq 
\begin{cases} 
e^{\alpha_k + \alpha_{k-1} - d_{k-1} + (b+\gamma)\tau_k} \overline{\Delta}(t_{k-2}), & \text{若 } \Delta(t_{k-1}) > \Delta_{t_0} \\ 
e^{\alpha_k + (b+\gamma)\tau_k} \Delta_{t_0}, & \text{若 } \Delta(t_{k-1}) \leq \Delta_{t_0} 
\end{cases}
$$

$$
\leq 
\begin{cases} 
e^{\alpha_k + \alpha_{k-1} - d_{k-1} + (b+\gamma)\tau_k} \Delta(t_{k-2}), & \text{若 } \Delta(t_{k-2}) > \Delta_{t_0}, \\ 
e^{\alpha_k + \alpha_{k-1} - d_{k-1} + (b+\gamma)\tau_k} \Delta_{t_0}, & \text{若 } \Delta(t_{k-2}) < \Delta_{t_0} < \Delta(t_{k-1}), \\ 
e^{\alpha_k + (b+\gamma)\tau_k} \Delta_{t_0}, & \text{若 } \Delta(t_{k-1}) \leq \Delta_{t_0}
\end{cases}
$$







还没有写完…反正也没人看qwq   很难绷就这点东西我捯饬了一晚上，依旧菜菜的。

感觉最近一直在为一些事情焦虑导致心情很不好…也许等我找到工作过上我期待的生活会好一点。但是真的会有那一天吗（？

好像失去了乐观的资本（
