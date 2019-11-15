###  1. RL介绍

> 强化学习（Reinforcement Learning，RL)，又称再励学习，评价学习或增强学习，是机器学习的范式和方法论之一，用于描述和解决智能体在于环境的交互过程中通过学习策略以达成回报最大化或实现特性目标的问题。 

- 基本要素

$$
\begin{align}
& A：动作空间（Action space) \\
& S：状态空间（State spcae) \\
& R：奖励（Reward) \\
& P：状态转移概率矩阵（Transition）
\end{align}
$$

### 2.马尔科夫决策过程（Markov Decision Process, MDP ）

#### 2.1 马尔科夫过程（Markov Process)

> 在一个随机过程$ s_0,s_1,...,s_n $中，已知时刻$t_i$所处的状态$s_i$，如果在时刻$t_{i+1}$时的状态$s_{i+1}$至于状态$s_i$相关，耳语$t_i$时刻之前的状态无关，则称这个过程为马尔科夫过程。
>
> 具有马尔科夫性质的随机过程$s_0,s_1,...,s_n$成为马尔科夫链。

#### 2.2 马尔科夫回报过程（Markov Reward Process)

状态```s```的期望奖励值表示为
$$
V(s)=E[G_t|S_t=s],其中V表示奖励的期望
$$
计算累计奖励的方式

- 计算从当前状态到结束状态的所有奖励之和,适合**有限时界强**库抗下的强化学习
  $$
  \begin{align}
  V(s)&=E[G_t|S_t=s] \\
  & =E[r_{t+1}+r_{t+2}+...+r_{t+T}] \\
  & =E[r_{t+1}+V(S_{t+1})|S_t=s] \\
  & =\sum _{s^·}P(s^`|s)(R(s^`)+V(s^`))
  \end{align}
  $$

- 增加折扣因子，适合**无限时界**
  $$
  \begin{align}
  V(s)&=E[G_t|S_t=s] \\
  & =E[r_{t+1}+\gamma r_{t+1}+\gamma^2r_{t+3}+...] \\
  & =E[r_{t+1}+\gamma V(S_{t+1})|S_t=s] \\
  & =\sum _{s^`}P(s^`|s)(R(s^`)+\gamma V(s^`))
  \end{align}
  $$
  

#### 2.3 马尔科夫决策过程（Markov Decision Process，MDP）

将马尔科夫决策过程定义为一个五元组：
$$
\begin{align}
& M=(S,A,R,P,\gamma) \\
& S:状态空间，表示所有的状态 \\
& A：动作空间，表示每个状态下可执行的动作 \\
& R:S*A \rightarrow R,奖励函数 \\
& P:S*A \rightarrow S,状态转移规则
\end{align}
$$
**强化学习要解决的问题是：agent(智能体)需要学习一个策略（policy）$ \pi $ ,这个策略$ \pi $定义了从状态到动作的一个映射关系$ \pi :S \rightarrow A$,也就是说，agent在任意状态$s_t$下所能执行的动作为：$a_t=\pi (s_t)$,并且有**
$$
\sum _{a_t \in A} \pi (a_t|s_t)=1
$$




