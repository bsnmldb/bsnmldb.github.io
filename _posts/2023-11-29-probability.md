---
title: 'A Concise Introduction to Probability Theory'
date: 2023-11-29
permalink: /posts/2023/11/probability/
tags:
  - probability theory
---

This is a straightforward introduction to probability theory, including combinatorial analysis, random variables, and more.

# 组合分析

计算一个事件发生结果的数目分析事件的概率

## 计数基本法则

乘法计数

## 排列

n个元素排列	$n!$

n个元素, $n_1$个不可区分, $n_2$不可区分, ..., $n_r$个不可区分 $(\sum_i^r n_i=n)$ 	$\frac{n!}{n_1!n_2!...n_r!}$

(先排列, 再在每组中去掉重复排列的部分, 即除以$n_i!$)

 ## 组合

### n个元素取出r个

$$
\tbinom{n}{r}=\frac{n!}{(n-r)!r!}
$$
### 组合恒等式

$$
\tbinom{n}{r}=\tbinom{n-1}{r-1}+\tbinom{n-1}{r}
$$
### 二项式定理

$$
(x+y)^n=\sum_{k=0}^n\tbinom{n}{k}x^ky^{n-k}
$$

## 多项式系数

n个不同的元素, 分成r组, 每组分别有 $n_1, n_2, ..., n_r$ 个元素, 其中$\sum_i^r n_i=n$ 

(先从n个里选出$n_1$个, 依次选下去)
$$
\tbinom{n}{n_1}\tbinom{n-n_1}{n_2}...\tbinom{n-n_1-n_2-...-n_{r-1}}{n_r}=\frac{n!}{n_1!n_2!...n_r!}
$$
> 考虑与排列中例子的等价性

### 定义

$$
\tbinom{n}{n_1,n_2,...,n_r}=\frac{n!}{n_1!n_2!...n_r!}
$$
### 多项式定理

$$
(x_1+x_2+...+x_r)^n=\sum\tbinom{n}{n_1,n_2,...,n_r}x_1^{n_1}x_2^{n_2}...x_r^{n_r}
$$
遍历所有满足 $\sum_i^r n_i=n$ 的 $(n_1,n_2,...,n_r)$ 非负向量

## 方程整数解的个数

对正整数向量$(n_1,n_2,...,n_r)$, $\sum_i^r n_i=n$ , 共$\tbinom{n-1}{r-1}$ 种

对非负向量$(n_1,n_2,...,n_r)$, $\sum_i^r n_i=n$ , 共$\tbinom{n-1+r}{r-1}$ 种



# 概率论公理化

- 样本空间 $S$ , 所有可能的结果构成的集合

- 事件 $E$ , 样本空间的任一子集

- 事件的交和并, 及交换律, 结合律, 分配律, 德摩根律

- 事件$E\ F$互不相容, $EF=\emptyset$

- 补事件$E^c$ 

- 包含

- 事件相等 $E=F \Leftrightarrow E\sub F \  and\  F\sub E$


## 公理

### 频率定义概率, 在样本空间$S$中, 对事件$E$

$$
P(E)=\lim_{n\rightarrow \infty}\frac{n(E)}{n}
$$
问题: 极限一定收敛于一个常数? 不同的实验中, 趋向同一个值?

### 现代概率论

$$
公理1\quad 0\leqslant P(E)\leqslant 1\\
公理2\quad P(S)=1\\
公理3\quad 对任一系列互不相容的事件E_1, E_2, ...(即 i\neq j, E_iE_j=\empty), 有\\
P(\cup_{i=1}^\infty E_i)=\sum_{i=1}^\infty P(E)
$$
把满足上述三条公理的$P(E)$称为事件$E$的概率

### 公理的推论

+ $$
  E_1=S,\ E_i=\empty(i>1) \Rightarrow P(\empty)=0
  $$

+ $$
  E_i=\empty(i>n)\Rightarrow P(\cup_{i=1}^n E_i)=\sum_{i=1}^n P(E)\ (事件互不相容)
  $$

+ $$
  P(E^c)=1-P(E)
  $$

+ $$
  E\sub F\Rightarrow P(E)\leqslant P(F)
  $$

+ $$
  P(E\cup F)=P(E)+P(F)-P(EF)
  $$

  > 容斥恒等式

## 等可能的样本空间

样本空间$S$为有限集, $S={1,2,3,..., n}$
$$
P({1})=P({2})=...=P({N})\\
P({i})=\frac{1}{N}\\
P(E)=\frac{|E|}{|S|}
$$

## 连续集函数



+ 递增(递减)列

  ​	一列事件$\set{E_n|n\geq 1}$ 称为递增列, 若

  ​	
  $$
  E_1\sub E_2 \sub ...\sub E_n \sub E_{n+1} \sub ...
  $$
  ​		反之称为递减列, 如果
  $$
  E_1\supset E_2 \supset ...\supset E_n \supset E_{n+1} \supset ...
  $$

+ 对递增事件列定义事件
  $$
  \lim_{n\rightarrow \infty} E_n=\cup_{i=1}^\infty E_i
  $$
  
+ 对递减事件列定义事件
  $$
  \lim_{n\rightarrow \infty} E_n=\cap_{i=1}^\infty E_i
  $$
  
+ 有
  $$
  \lim_{n\rightarrow \infty} P(E_n)=P(\lim_{n\rightarrow \infty} E_n)
  $$
  

## 概率: 确信程度的度量(主观概率)

与频率主义相区别

但是无论是频率主义还是主观概率, 都满足概率论公理, 数学属性不变

# 条件概率

### 在事件 $F$ 下 $E$ 发生的概率

$$
P(E|F)
$$
### 定义

$$
P(E|F)=\frac{P(EF)}{P(F)}
$$
### 乘法规则

$$
P(E_1E_2...E_n)=P(E_1)P(E_2|E_1)P(E_3|E_2E_1)...P(E_n|E_1...E_{n-1})\\
特别地\quad P(E_1E_2)=P(E_1)P(E_2|E_1)=P(E_2)P(E_1|E_2)
$$

> B C 为例子

## 贝叶斯公式

### 全概公式

$$
E=EF\cup EF^c\quad 且两者互不相容\\

P(E)=P(EF)+P(EF^c)\\
=P(E|F)P(F)+P(E|F^c)P(F^c)\\
=P(E|F)P(F)+P(E|F^c)[1-P(F)]\\
\\
P(E)=P(E|F)P(F)+P(E|F^c)[1-P(F)]
$$

用 $F$ 事件的加权平均来计算事件 $E$

### 优势

+ 发现证据更新认知和判断

事件 $A$ 的优势定义为
$$
\frac{P(A)}{P(A^c)}=\frac{P(A)}{1-P(A)}
$$
当发现新的证据时, 假设成立的概率之变化可以表示为其优势之变化

在证据 $E$ 之下, 假设 $H$ 的变化
$$
\frac{P(H|E)}{P(H^c|E)}=\frac{P(H)}{P(H^c)}\frac{P(E|H)}{P(E|H^c)}
$$

### 全概公式的推广 $\Rightarrow$ 贝叶斯公式

一组完备事件 $F_i(i=1,2,...,n)$ , 即 $F_i$ 为互不相容事件 且 $\cup F_i=S$(必然事件)

$P(E)=\sum_{i=1}^n P(EF_i)=\sum_{i=1}^n P(E|F_i)P(F_i)$

$P(E)$ 关于完备事件 $F$ 加权
$$
P(F_j|E)=\frac{P(EF_j)}{P(E)}=\frac{P(E|F_j)P(F_j)}{\sum_{i=1}^n P(E|F_i)P(F_i)}
$$


## 独立事件

### 定义

对于两个事件 $E$ 和 $F$ , 若 $P(EF)=P(E)P(F)$ 成立, 称它们是独立的, 反之, 称为相依的/相互不独立的

### 推论

若两个事件 $E$ 和 $F$ 相互独立, 那么事件 $E$ 和 $F^c$ 也相互独立
$$
P(EF)=P(E)P(F)\\
P(EF^c)=P(E)-P(EF)=P(E)[1-P(F)]=P(E)P(F^c)
$$

### 推广1(三个事件)

如果事件 $E F G$ 相互独立, 如果 
$$
P(EFG)=P(E)P(F)P(G)\quad (1)\\
P(EF)=P(E)P(F)\quad (2)\\
P(EG)=P(E)P(G)\quad (3)\\
P(FG)=P(F)P(G)\quad (4)
$$

> 考虑(1)与(2)(3)(4)之间的关系!



### 推广2(三个事件以上)

事件 $E_1, E_2, E_3, ... , E_n$ 相互独立, 如果对于这些事件的任意子集 $E_{1^*}, E_{2^*},...,E_{r^*}, r\leq n$, 都有
$$
P(E_{1^*}E_{2^*}...E_{r^*})=P(E_{1^*})P(E_{2^*})...P(E_{r^*})
$$


###  推广3(无限个事件)

无限个事件的任意有限个子集都是独立的

### 条件独立性

事件 $E_1$ 和 $E_2$ 对于给定事件 $F$ 是条件独立的, 如果
$$
P(E_1|E_2F)=P(E_1|F)
$$

> 在 $F$ 发生的条件下, $E_1$ 发生的概率不因 $E_2$ 发生与否而改变

等价地
$$
P(E_1E_2|F)=P(E_1|E_2F)P(E_2|F)=P(E_1|F)P(E_2|F)
$$


## 重复试验

所考虑的概率是一系列子试验, 且这一系列子试验相互独立

若各个子试验彼此相同, 即各子试验有相同的(子)样本空间及相同的事件概率函数, 那么称这些试验为重复试验

### 推论

独立重复试验中, $E$ 和 $F$ 为一次试验中两个互不相容的事件, 那么事件 $E$ 发生在 $F$ 之前的概率为
$$
P=1\cdot P(E)+P(1-P(E)-P(F))+0\cdot P(F)\\
\Rightarrow P=\frac{P(E)}{P(E)+P(F)}
$$



### problem of the points

假设在独立重复试验中, 每次成功的概率为 $P$ , 失败的概率为 $1-P$ , 问在 $m$ 次失败之前有 $n$ 次成功的概率

#### 帕斯卡

$P_{n,m}$ 表示在 $m$ 次失败之前有 $n$ 次成功, 那么有
$$
P_{n,m}=PP_{n-1,m}+(1-P)P_{n,m-1}\quad n\geqslant 1,\ m\geqslant 1\\
P_{n,0}=0\\
P_{0,m}=1
$$

#### 费马

相当于在 $m+n-1$ 次试验中至少有 $n$ 次成功

已知在 $m+n-1$ 次试验中恰有 $k$ 次成功的概率为 $\tbinom{m+n-1}{k}P^k(1-P)^{m+n-1-k}$ 

那么所求概率为
$$
P_{n,m}=\sum_{k=n}^{m+n-1}\tbinom{m+n-1}{k}P^k(1-P)^{m+n-1-k}
$$

#### 利用负二项分布

考虑第 $m$ 次成功发生的时刻不晚于 $m+n-1$ 次试验

##### 已知分布列

$$
P\set{X=n}=\tbinom{n-1}{r-1}p^r(1-p)^{n-r}
$$

##### 那么

$$
P\set{X\leqslant m+n-1}=\sum_{k=n}^{m+n-1}\tbinom{k-1}{n-1}p^n(1-p)^{k-n}
$$

### 赌徒破产问题

#### 赌博持续时间问题

### 拉普拉斯继承准则

### 序贯地补充信息

现在有 $n$ 个互不相容且完全的假设, 其初始概率[先验(prior)概率]为 $P(H_i),\quad \sum_{i=1}^nP(H_i)=1$ ,现在知道事件 $E_1$ 发生, 那么 $H_i$ 成立的条件概率[后验(posterior)概率]
$$
P(H_i|E)=\frac{P(E|H_i)P(H_i)}{\sum_j P(E|H_j)P(H_j)}
$$
 如果先知道 $E_1$ 后知道 $E_2$
$$
P(H_i|E_1E_2)=\frac{P(E_1E_2|H_i)}{\sum_j P(E_1E_2|H_j)P(H_j)}
$$

> 推广到序贯地补充信息

## 条件概率满足的性质

+ 满足概率的三条公理

+ 满足普通概率的所有性质

+ $$
  define\quad Q(E)=P(E|F)\\
  Q(E|R)=P(E|RF)
  $$

  



# 随机变量

随机变量(random variable)是定义在样本空间上试验结果的实值函数

## 累积分布函数

对于随机变量 $X$ , 定义函数 $F$ (cumulative distribution function)
$$
F(x)=P\set{X\leqslant x}\quad -\infty<x<\infty
$$

## 离散性随机变量

最多有可数多个可能取值

### 概率分布列(probability mass function)

$X$ 的概率分布列 $p(a)$
$$
p(a)=P\set{X=a}
$$

### 离散型随机变量的分布函数

$$
F(a)=\sum_{x:x\leqslant a}p(x)
$$

是跳跃的阶梯函数, 并非点集



## 期望

### 定义

随机变量 $X$ 的期望
$$
E[X]=\sum_{x:p(x)>0}xp(x)
$$

> $X$ 所有取值的加权平均, 权重为取值的概率

### 随机变量函数的期望

$X$ 为一个离散型随机变量, $g(X)$ 为另一个随机变量(也是一个随机变量函数)
$$
E[g(X)]=\sum_i g(x_i)p(x_i)
$$
特别地
$$
E[aX+b]=aE[X]+b
$$


## 方差

### 定义

$X$ 期望为 $\mu$ , 方差 $Var(X)$ 为
$$
Var(X)=E[(X-\mu)^2]
$$

### 推论

$$
Var(X)=E[X^2]-E[X]^2
$$

### 标准差

$$
SD(X)=\sqrt{Var(X)}
$$

## 示性变量

称 $I$ 是事件按 $A$ 的示性变量
$$
I=\begin{cases}
1\quad if\ A\ happens\\
0\quad if\ not 
\end{cases}
\\
E[I]=P(A)
$$

## 伯努利随机变量与二项随机变量

### 伯努利随机变量

单次试验

#### 随机变量

$$
X=\begin{cases}
1\quad succeed\\
0\quad fail
\end{cases}
$$

#### 分布列

$$
p(0)=P\set{X=0}=1-p\\
p(1)=P\set{X=1}=p\\
p\in (0,1)
$$

### 二项随机变量

#### 随机变量

进行 $n$ 次独立重复试验, 每次成功的概率为 $p$ , 失败的概率为 $1-p$ , $X$ 表示 $n$ 次独立重复试验成功的次数

称 $X$ 为参数为 $(n,p)$ 的二项随机变量(binomial)

> 伯努利随机变量也称为参数为 $(1,p)$ 的二项随机变量

#### 分布列

$$
p(i)=\tbinom{n}{i}p^i(1-p)^{n-i}\quad i=0,1,...,n
$$

### 二项随机变量的性质

参数为 $(n,p)$ 的二项随机变量

#### 期望

$$
E[X^k]=\sum_{i=0}^ni^k\tbinom{n}{i}p^i(1-p)^{n-i}=\sum_{i=1}^ni^k\tbinom{n}{i}p^i(1-p)^{n-i}
$$

利用 $i\tbinom{n}{i}=n\tbinom{n-1}{i-1}$
$$
E[X^k]=np\sum_{i=1}^ni^{k-1}\tbinom{n-1}{i-1}p^{i-1}(1-p)^{n-i}\\
=np\sum_{j=0}^{n-1}(j+1)^{k-1}\tbinom{n-1}{j}p^j(1-p)^{n-1-j}\quad\quad\quad j=i-1\\
=npE[(Y+1)^{k-1}]
$$
$Y$ 是一个参数为 $(n-1,p)$ 的二项随机变量



令 $k=1$
$$
E[X]=npE[(Y+1)^0]\\
\Rightarrow E[X]=np
$$
令 $k=2$
$$
E[X^2]=npE[Y+1]=np((n-1)p+1)\\
E[X^2]-E[X]^2=np((n-1)p+1)-(np)^2=np(1-p)\\
\Rightarrow Var(X)=np(1-p)
$$

##### 结论

$$
E[X]=np\\
Var(X)=np(1-p)
$$

#### 分布列

$P\set{X=k}, \quad k=0,1,2,...,n$ , 先递增, 后递减, 在 $k=\lfloor(n+1)p\rfloor (向下取整)$ 时取最大
$$
pf:构造\frac{P\set{X=k}}{P\set{X=k-1}}
$$

#### 二项分布函数

$$
F(i)=\sum_{k=0}^{\lfloor i\rfloor}\tbinom{n}{k}p^k(1-p)^{n-k}\quad \quad i=0,1,...,n
$$

利用递推关系
$$
P\set{X=k+1}=\frac{p}{1-p}\frac{n-k}{k+1}P\set{X=k}\\
P\set{X=0}=(1-p)^{n}
$$


## 泊松随机变量

### 定义

一个取值为 0,1,2,... 之一的随机变量称为服从参数为 $\lambda$ 的泊松随机变量(poisson), 如果存在 $\lambda>0$ , 有
$$
p(i)=P\set{X=i}=e^{-\lambda}\frac{\lambda^i}{i!}\quad \quad i=0,1,2,...
$$

> $$
> \sum_{i=0}^\infty e^{-\lambda}\frac{\lambda^i}{i!}=e^{-\lambda}\sum_{i=0}^\infty \frac{\lambda^i}{i!}=e^{-\lambda}e^\lambda=1
> $$

### 应用

对于参数为 $(n,p)$ 的二项分布, 当 $n$ 足够大, $p$ 充分小, 而使得 $np$ 保持适当大小时, 该二项分布可近似看作泊松分布, 且 $\lambda =np$
$$
P\set{X=i}=\tbinom{n}{i}p^i(1-p)^{n-i}=\frac{n!}{(n-i)!i!}(\frac{\lambda}{n})^i(1-\frac{\lambda}{n})^{n-i}\\
=\frac{n(n-1)...(n-i+1)}{n^i}\frac{\lambda^i}{i!}\frac{(1-\frac{\lambda}{n})^n}{(1-\frac{\lambda}{n})^i}
$$
对于充分大的 $n$ 和适当的 $\lambda$ , 有
$$
(1-\frac{\lambda}{n})^n\approx e^{-\lambda}\\
\frac{n(n-1)...(n-i+1)}{n^i}\approx 1\\
{(1-\frac{\lambda}{n})^i}\approx 1\\
\Rightarrow P\set{X=i}\approx e^{-\lambda}\frac{\lambda^i}{i!}
$$

> example 1 二项分布
>
> 一本书某一个字印刷错误
>
> ​	一本书有很多字(n充分大)
>
> ​	某个字印刷错误的概率很小(p很小)
>
> example 2 试验不独立但弱相依 
>
> 拿帽子匹配问题
>
> n个人过生日问题



### 期望

$$
E[X]=\sum_{i=0}^\infty ip(i)=\sum_{i=1}^\infty \frac{ie^{-\lambda}\lambda^i}{i!}\\
=\sum_{i=1}^\infty \frac{e^{-\lambda}\lambda^i}{(i-1)!}=\lambda\sum_{i=0}^\infty\frac{e^{-\lambda}\lambda^i}{i!}\\
=\lambda
$$



### 方差

$$
E[X^2]=\sum_{i=1}^\infty \frac{i^2e^{-\lambda}\lambda^i}{i!}=\lambda\sum_{i=0}^\infty\frac{(i+1)e^{-\lambda}\lambda^i}{i!}\\
=\lambda\Bigg[\sum_{i=0}^\infty\frac{ie^{-\lambda}\lambda^i}{i!}+\sum_{i=0}^\infty\frac{e^{-\lambda}\lambda^i}{i!}\Bigg]=\lambda(\lambda +1)\\
Var(X)=E[X^2]-E[X]^2\\\\
Var(X)=\lambda
$$

### 泊松范例

如果 $n$ 个事件, 每个事件发生的概率为 $p_i,i=1,2,...,n$ , 所有的 $p_i$ 都很小, 且试验或者独立, 或至多弱相依, 那么事件发生次数近似服从参数为 $\sum_{i=1}^n p_i$ 的泊松分布

### 发生在一列(随机)时间点上的事件

事件发生在某些时间点上, 假设在一列随机的时间点上, 并存在某个正的常数 $\lambda$

+ 在任意长度为 $h$ 的时间区间内, 正好发生一个事件的概率彼此相同, 且为 $\lambda h+o(h)$

+ 在任意长度为 $h$ 的时间区内发生2个或更多个时间的概率非常小, 等于 $o(h)$

+ 对于任意确定的自然数 $n$ 与非负整数 $j_1,j_2,...,j_n$ , 以及任意 $n$ 个互不相交的时间区间内, 若以 $E_i$ 表示在 $i$ 个时间区间内上述事件正好发生 $j_i$ 次, 则 $E_1, E_2, ..., E_n$ 相互独立

  > 在一个时间区间内无论发生了什么, 对另一个与它不相交的区间在概率意义上没有影响

在此假设下, 在任意长度为 $t$ 的时间区间内, 时间发生的次数是以 $\lambda t$ 为参数的泊松随机变量

称事件是按速率为 $\lambda$ 为泊松过程发生的, 即单位时间内事件发生的速率

> 证明略

### 泊松分布函数

利用递推式
$$
\frac{P\set{X=i+1}}{P\set{X=i}}=\frac{\lambda}{i+1}\\
P\set{X=0}=e^{-\lambda}\\
P\set{X=1}=\lambda P\set{X=0}\\
P\set{X=2}=\frac{\lambda}{2}P\set{X=1}\\
...\\
$$

 ## 几何随机变量

### 定义

独立重复试验, 每次成功率为 $p,0<p<1$ ,一直进行直到试验成功, $X$ 表示试验总次数

### 分布列

$$
P\set{X=n}=(1-p)^{n-1}p\quad \quad n=1,2,...
$$

 ### 一定会结束

$$
\sum_{n=1}^\infty P\set{X=n}=p\sum_{n=1}^\infty(1-p)^{n-1}=\frac{p}{1-(1-p)}=1
$$

### 期望

$$
E[X]=\sum_{n=1}^\infty n(1-p)^{n-1}p=\sum_{n=1}^\infty (n-1+1)(1-p)^{n-1}p\\
=\sum_{n=1}^\infty (n-1)(1-p)^{n-1}p+\sum_{n=1}^\infty (1-p)^{n-1}p\\
=(1-p)\sum_{n=1}^\infty n(1-p)^{n-1}p+1=(1-p)E[X]+1\\
\Rightarrow E[X]=\frac{1}{p}
$$

### 方差

$$
E[X^2]=\sum_{n=1}^\infty n^2(1-p)^{n-1}p=\sum_{n=1}^\infty (n-1+1)^2(1-p)^{n-1}p\\
=\sum_{n=1}^\infty (n-1)^2(1-p)^{n-1}p+\sum_{n=1}^\infty 2(n-1)(1-p)^{n-1}p+\sum_{n=1}^\infty (1-p)^{n-1}p\\
=(1-p)E[X^2]+2(1-p)E[X]+1\\
\Rightarrow E[X^2]=\frac{2-p}{p^2}\\
Var(x)=\frac{2-p}{p^2}-\frac{1}{p}\\
\Rightarrow Var(x)=\frac{1-p}{p^2}
$$

## 负二项分布

### 定义

独立重复试验, 每次成功率为 $p,0<p<1$ ,一直进行直到试验成功 $r$ 次为止, $X$ 表示试验总次数

满足下面的分布列的随机变量 $X$ 服从参数为 $(r,p)$ 的负二项分布(negative binomial)

> 几何分布是参数为 $(1,p)$ 的负二项分布

### 分布列

$$
P\set{X=n}=\tbinom{n-1}{r-1}p^r(1-p)^{n-r}
$$

> 解决 the problem of the point

### 一定能成功

#### 分析法

$$
\sum_{n=r}^\infty P\set{X=n}=1
$$

#### 概率论证

转化为几何分布



### 期望

$$
E[X^k]=\sum_{n=r}^\infty n^k\tbinom{n-1}{r-1}p^r(1-p)^{n-r}
$$

化简
$$
E[X^k]=\frac{r}{p}E[(Y-1)^{k-1}]
$$
其中 $Y$ 是一个以 $(r+1,p)$ 为参数的负二项随机变量

令 $k=1$
$$
E[X]=\frac{r}{p}
$$

### 方差

令 $k=2$
$$
E[X^2]=\frac{r}{p}E[Y-1]=\frac{r}{p}\Big(\frac{r+1}{p}-1\Big)\\
Var(X)=E[X^2]-E[X]^2=\frac{r(1-p}{p^2}
$$


## 超几何随机变量

### 定义

$N$ 个球, $m$ 个白色, $N-m$ 个黑色, 取大小为 $n$ 的样本, $X$ 表示取出的白球数

参数为 $(n,N,m)$

### 分布列

$$
P\set{X=i}=\frac{\tbinom{m}{i}\tbinom{N-m}{n-i}}{\tbinom{N}{n}}\quad \quad i=0,1,...,n
$$

### 近似二项分布

当对于 $n$ , $N$ 和 $m$ 很大时, 近似等于参数为 $(n,p),p=\frac{m}{N}$ 的二项分布

###  期望

$$
E[X^k]=\sum_{i=1}^ni^k\tbinom{m}{i}\tbinom{N-m}{n-i}/\tbinom{N}{n}\\
=\frac{nm}{N}E[(Y+1)^{k-1}]
$$

其中, Y是服从参数为 $(n-1,N-1,m-1)$ 的超几何分布的随机变量

令 $k=1$
$$
E[X]=\frac{nm}{N}=np
$$


### 方差

令 $k=2$
$$
E[X^2]=\frac{nm}{N}E[Y+1]=\frac{nm}{N}\Big[\frac{(n-1)(m-1)}{N-1}+1\Big]\\
Var(X)=np(1-p)\bigg(1-\frac{n-1}{N-1}\bigg)\\
p=\frac{m}{N}
$$

> 当 $N$ 很大时, $Var(X)\approx np(1-p)$



## zeta 分布(Zipf)

$\zeta$ 分布(Zipf)

### 分布列

$$
P\set{X=k}=\frac{C}{k^{\alpha +1}}\quad \quad k=1,2,...
$$

其中, $\alpha >0$ 为参数, 且由于概率之和为1
$$
C=\Bigg[\sum_{k=1}^\infty (\frac{1}{k})^{\alpha +1}\Bigg]^{-1}
$$


## 随机变量和与期望

### 期望的线性性

#### 引理

$$
E[X]=\sum_{s\in S}X(s)p(s)
$$

#### 结论

对于随机变量 $X_1,X_2,...,X_n$ ,下式成立
$$
E\Bigg[\sum_{i=1}^nX_i \Bigg]=\sum_{i=1}^nE[X_i]
$$

## 分布函数的性质

+ 非降函数 $F(b)=P\set{X\leqslant b}$
+ $\lim\limits_{b\rightarrow +\infty}F(b)=1$
+ $\lim\limits_{b\rightarrow -\infty}F(b)=0$
+ 右连续
+ $P\set{a<X\leqslant b}=F(b)-F(a)$
+ $P\set{X< b}=P\set{\lim\limits_{n\rightarrow\infty}(X\leqslant b-\frac{1}{n})}=\lim\limits_{n\rightarrow\infty}P\set{X\leqslant b-\frac{1}{n}}=\lim\limits_{n\rightarrow\infty}F(b-\frac{1}{n})$



# 连续型随机变量

## 介绍

### 回顾

离散型随机变量可能取值的个数是有限的或者可数无限的

### 定义

连续性随机变量可能取值是无限不可数的(大小为阿列夫1)

有概率密度函数

### 概率密度函数

定义在实数轴上的非负函数 $f$ , 使得对于任一 $\mathbb{R}$ 的子集 $B$ 都有
$$
P\set{X\in B}=\int_Bf(x)dx
$$
满足
$$
\int_\mathbb{R}f(x)dx=1\\\\
P\set{a\leqslant X\leqslant b}=\int_a^bf(x)dx\\\\
P\set{X=a}=0
$$
注意到连续型随机变量取任意固定值的概率都为0

分布函数
$$
F(a)=\int_{-\infty}^af(x)dx
$$

## 期望

$$
E[X]=\int_{-\infty}^{+\infty}xf(x)dx
$$

### 连续性随机变量函数的期望

#### 定理

$$
E[g(X)]=\int_{-\infty}^{+\infty}g(x)f(x)dx
$$

#### 转换

令随机变量 $Y=g(X)$ , 求其分布函数
$$
F_Y(x)=P\set{Y\leqslant x}=\int_{when\  Y\leqslant x}f(t)dt
$$
求导得到 $Y$ 的概率密度函数 $f_Y$
$$
E[Y]=\int_{-\infty}^{+\infty}yf_Y(y)dy
$$

#### 随机变量函数的线性性质

$$
E[aX+b]=aE[X]+b
$$

## 方差

同离散型随机变量

期望值为 $\mu$ 时
$$
Var(X)=E[(X-\mu)^2]\\
Var(X)=E[X^2]-E[X]^2
$$

### 线性性

$$
Var(aX+b)=a^2Var(X)
$$



## 均匀分布的随机变量

### 定义

一个随机变量称为服从 $(0,1)$ 区间上的均匀分布, 如果其概率密度函数为
$$
f(x)=\begin{cases}
1\quad 0<x<1\\
0\quad else
\end{cases}
$$
服从 $(\alpha,\beta)$ 区间上的均匀分布
$$
f(x)=\begin{cases}
\frac{1}{\beta -\alpha}\quad \alpha <x<\beta\\
0\quad else
\end{cases}\\\\
F(x)=\begin{cases}
0\quad x\leqslant \alpha \\
\frac{x-\alpha}{\beta -\alpha}\quad \alpha <x<\beta\\
1\quad x\geqslant \beta
\end{cases}
$$

### 期望

$$
E[X]=\int_\alpha^\beta xf(x)dx=\int_\alpha^\beta \frac{x}{\beta -\alpha}dx\\
=\frac{\frac{1}{2}(\beta^2 -\alpha^2)}{\beta -\alpha}=\frac{\beta +\alpha}{2}
$$

### 方差

$$
E[X^2]==\int_\alpha^\beta x^2f(x)dx=\int_\alpha^\beta \frac{x}{\beta -\alpha}dx\\
=\frac{\frac{1}{3}(\beta^3 -\alpha^3)}{\beta -\alpha}=\frac{\beta^2 +\alpha\beta +\alpha^2}{3}\\\\
Var(X)=\frac{(\beta -\alpha)^2}{12}
$$



## 正态随机变量

### 定义

服从参数为 $\mu$ 和 $\sigma^2$ 正态分布的随机变量, 其概率密度函数
$$
f(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-(x-\mu)^2/2\sigma^2}
$$
关于 $x=\mu$ 对称

#### 归一化条件

$$
\int_{-\infty}^{+\infty}\frac{1}{\sqrt{2\pi}\sigma}e^{-(x-\mu)^2/2\sigma^2}dx=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{+\infty}e^{-(x-\mu)^2/2\sigma^2}d\frac{x-\mu}{\sigma}\\
=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{+\infty}e^{-y^2/2}dy=1
$$

#### 线性

若 $X$ 服从参数为 $\mu$ 和 $\sigma^2$ 正态分布, 那么 $aX+b$ 服从参数为 $a\mu+b$ 和 $a^2\sigma^2$ 正态分布

#### 标准正态随机变量

服从参数为 $\mu=0$ 和 $\sigma^2=1$ 正态分布的随机变量

在上述结论下, 对于任意的服从参数为 $\mu$ 和 $\sigma^2$ 正态分布随机变量 $X$ , $Z=(X-\mu)/\sigma$ 为标准正态随机变量

##### 概率密度函数

$$
\frac{1}{\sqrt{2\pi}}e^{-x^2/2}
$$

##### 分布函数

$$
\Phi(x)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^xe^{-y^2/2}dy\\\\
F(x)=\Phi(\frac{a-\mu}{\sigma})
$$



### 期望与方差

#### 标准正态随机变量

$$
E[Z]=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{+\infty}xe^{-x^2/2}dx=-\frac{1}{\sqrt{2\pi}}e^{-x^2/2}\bigg|_{-\infty}^{+\infty}=0\\\\
Var(Z)=E[Z^2]-0=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{+\infty}x^2e^{-x^2/2}dx\\
=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{+\infty}e^{-x^2/2}dx=1
$$

#### $X=\mu + \sigma Z$

$$
E[X]=\mu\\
Var(X)=\sigma^2
$$



### 二项分布的正态近似

对于二项分布, 当 $n$ 很大时, 近似于参数为 $(np,np(1-p))$ 的正态分布

也即对于参数为 $(n,p)$ 的二项分布, 成功次数为 $S_n$ , 当 $n\rightarrow \infty$ 时
$$
P\set{a\leqslant\frac{S_n-np}{\sqrt{np(1-p)}}\leqslant b}\rightarrow\Phi(b)-\Phi(a)
$$

> 当 $n$ 较大, 而 $p$ 较小时, 泊松近似很好
>
> 但当 $np(1-p)$ 较大时, 正态近似相当好

### 对数正态随机变量

$Y=e^X$ , 其中 $e^X$ 或者 $ln(Y)$ 为参数为 $(\mu,\sigma^2)$ 的正态随机变量, $Y$ 为参数为 $(\mu,\sigma^2)$ 的对数正态随机变量



## 指数随机变量

$X$ 为参数为 $\lambda>0$ 的指数分布的随机变量, 如果有概率密度函数
$$
f(x)=
\begin{cases}
\lambda e^{-\lambda x}\quad x\geqslant 0\\
0\quad x<0
\end{cases}
$$
分布函数
$$
F(x)=P\set{X\leqslant x}=\int_0^x\lambda e^{-\lambda x}dx=1-e^{-\lambda x}\quad x\geqslant 0
$$

### 期望与方差

$$
E[X^n]=\int_0^{+\infty}x^n\lambda e^{-\lambda x}dx=\frac{n}{\lambda}E[X^{n-1}]\\
E[X]=\frac{1}{\lambda}\\
E[X^2]=\frac{2}{\lambda^2}\\
Var(X)=\frac{1}{\lambda^2}
$$

### 应用

常作为某个事件发生的等待时间的分布而出现



### 无记忆的(memoryless)

#### 定义

称一个非负随机变量 $X$ 是无记忆的, 如果
$$
P\set{X>s+t|X>t}=P\set{X>t}\quad for\ all\ s,t\geqslant0
$$

#### 指数随机变量是无记忆的

$$
P\set{X>s+t}=P\set{X>s}+P\set{X>t}
$$

> 并且指数分布是唯一无记忆的分布



### 危险率函数

#### 定义

对一个正连续性随机变量 $X$ , 分布函数 $F$ , 分布密度 $f$ , 其危险率(hazard rate)/失效率(failure rate)为
$$
\lambda(t)=\frac{f(t)}{\overline{F}(t)}\quad \overline{F}=1-F
$$

#### 意义

考虑一个零件已经使用了时间 $t$ , 随机变量表示该零件的寿命
$$
P\set{X\in (t,t+dt)|X>t}=\frac{P\set{X\in (t,t+dt)\ \wedge\ X>t}}{P\set{X>t}}\approx\lambda(t)dt
$$
 表示 $dt$ 时间内, 该零件失效的概率

#### 对于无记忆的指数分布

一个有年龄的零件失效率与新零件相同
$$
\lambda(t)=\lambda
$$


#### 危险率能够唯一确定分布函数

对于正连续型随机变量
$$
\lambda(t)=\frac{\frac{d}{dt}F(t)}{1-F(t)}
$$


## 拉普拉斯随机变量

### 密度函数

$$
f(x)=\frac{1}{2}\lambda e^{-\lambda |x|}\quad -\infty < x < +\infty
$$

### 分布函数

$$
F(x)=\begin{cases}
\frac{1}{2}\int_{-\infty}^x \lambda e^{\lambda x}dx\\
\frac{1}{2}\int_{-\infty}^0\lambda e^{\lambda x}dx + \frac{1}{2}\int_0^x\lambda e^{\lambda x}dx
\end{cases}=
\begin{cases}
\frac{1}{2} e^{\lambda x},\quad x<0\\
1-\frac{1}{2} e^{-\lambda x},\quad x>0
\end{cases}
$$



## 瑞利分布

### 定义

具有线性危险率函数
$$
\lambda(t)=a+bt\\
F(t)=1-e^{-at-\frac{1}{2}bt^2}\\
f(t)=(a+bt)e^{-(at+\frac{1}{2}bt^2)}\quad t\geqslant 0
$$
$a=0$ 时, 为瑞利(Rayleigh)分布

### 与正态分布的关系?

![](https://raw.githubusercontent.com/bsnmldb/tuchuang/main/img/20220713170843.png)

![](https://raw.githubusercontent.com/bsnmldb/tuchuang/main/img/20220713171337.png)

![](https://raw.githubusercontent.com/bsnmldb/tuchuang/main/img/20220713170933.png)



## Gamma 分布

$\Gamma$ 分布

### 密度函数

参数为 $(\alpha,\lambda),\alpha>0,\lambda>0$ 
$$
f(x)=\begin{cases}
\frac{\lambda e^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma (\alpha)}\quad x\geqslant 0\\
0\quad x<0
\end{cases}\\
\Gamma(\alpha)=\int_0^{\infty}e^{-y}y^{\alpha-1}dy\\
\Gamma(n)=(n-1)\Gamma(n-1)\\
\Gamma(1)=1\\
\Gamma(n)=(n-1)!
$$

### 退化为指数分布

$\alpha=1$ 时, 
$$
f(x)=\lambda e^{-\lambda x}\quad x\geqslant 0
$$

### 与泊松分布(离散型的分布)的关系

#### 回顾泊松分布

$$
p(i)=P\set{X=i}=e^{-\lambda}\frac{\lambda^i}{i!}\quad \quad i=0,1,2,...
$$

在任意长度为 $t$ 的时间区间内, 时间发生的次数是以 $\lambda t$ 为参数的泊松随机变量

#### 考虑

参数为 $(\alpha,\lambda),\alpha为整数$ 的 $\Gamma$ 分布总是作为某件事发生 $n$ 次的等待时间(满足泊松分布的假设). 记 $T_n$ 表示第 $n$ 个事件发生的时间, $T_n\leqslant t$ 等价于在 $t$ 时间内, 发生的事件数量大于等于 $n$
$$
P\set{T_n\leqslant t}=P\set{N(t)\geqslant n}=\sum_{j=n}^\infty P\set{N(t)=j}=\sum_{j=n}^\infty e^{-\lambda t}\frac{(\lambda t)^j}{j!}(泊松分布)
$$
对 $t$ 求导
$$
f(t)=\frac{\lambda e^{-\lambda x}(\lambda x)^{n-1}}{(n-1)!}
$$
服从参数为 $(n,\lambda)$ 的 $\Gamma$ 分布

### 卡方分布

$\chi^2$ (卡方)分布

参数为 $(\frac{n}{2},\frac{1}{2})$ 的 $\Gamma$ 分布, 称为自由度为 $n$ 的 $\chi^2$ (卡方)分布

## 威尔布分布



## 柯西分布



## beta 分布

$\pmb{\beta}$ 分布

### 密度函数

$$
f(x)=\begin{cases}
\frac{1}{B(a,b)}x^{(a-1)}(1-x)^{b-1}\quad 0<x<1\\
0\quad else
\end{cases}\\\\
B(a,b)=\int_0^1x^{(a-1)}(1-x)^{b-1}dx=\frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}
$$



### 期望和方差

$$
E[X]=\frac{a}{b}\\
Var(X)=\frac{ab}{(a+b)^2(a+b+1)}
$$

### 均匀分布

当参数 $(a=1,b=1)$ 时, 退化为 $(0,1)$ 的均匀分布

即 $\frac{1}{B(1,1)}x^{(1-1)}(1-x)^{1-1}=1$



### 直观认识?

![](https://raw.githubusercontent.com/bsnmldb/tuchuang/main/img/QQ%E5%9B%BE%E7%89%8720220713164228.png)

![](https://raw.githubusercontent.com/bsnmldb/tuchuang/main/img/20220713164741.png)

## 随机变量函数的分布

对于连续随机变量 $X$ , 密度函数 $f_X$ , 假设 $g$ 为一个严格单调且可微(因此连续)的函数, 那么随机变量 $Y$ 的密度函数为
$$
f_Y=\begin{cases}
f_X\big[g^{-1}(y)\big]\bigg|\frac{d}{dy}g^{-1}(y)\bigg|\quad \exist x,\ y=g(x)\\
0\quad else
\end{cases}
$$




# 随机变量的联合分布

## 联合分布函数

随机变量 $X$ 和 $Y$ 的联合分布函数(joint cummulative probability distribution function)

### 连续性随机变量

$$
F(a,b)=P\set{X\leqslant a,Y\leqslant b}\quad -\infty <a,b< +\infty
$$

其中
$$
F_X(a)=F(a,+\infty)\\
F_Y(b)=F(+\infty,b)
$$
$F_X\ F_Y$ 称为 $X\ Y$ 的边缘分布(marginal distribution)

计算概率问题
$$
P\set{X>a,Y>b}=1-F_X(a)-F_Y(b)+F(a,b)\\
P\set{a_1<X\leqslant a_2,b_1<Y\leqslant b_2}=F(a_2,b_2)+F(a_1,b_1)-F(a_1,b_2)-F(a_2,b_1)
$$

### 离散随机变量

联合分布列(joint probability mass function)
$$
p(x,y)=P\set{X=x,Y=y}\\
p_X(x)=P\set{X=x}=\sum_{y:p(x,y)>0}p(x,y)
$$

### 联合连续

称 $X$ 和 $Y$ 是联合连续的,如果存在一个对任意 $x,y$ 定义的函数 $f(x,y)$ ,对任意实数对集合 $C\sub \mathbb{R}^2$
$$
P\set{(X,Y)\in C}=\iint_{(x,y)\in C}f(x,y)dxdy
$$
其中, $f$ 为 $X$ 和 $Y$ 的联合密度函数(joint probability density function)

如果 $C=A\times B$ ,那么
$$
P\set{(X,Y)\in C}=\int_B\int_Af(x,y)dxdy\\
F(a,b)=P\set{X\in (-\infty,a),Y\in (-\infty,b)}=\int_{-\infty}^b\int_{-\infty}^af(x,y)dxdy\\
f(a,b)=\frac{\partial^2}{\partial a\partial b}F(a,b)\\
f_X(x)=\int_{-\infty}^{+\infty}f(x,y)dy
$$

### 多个随机变量的联合分布 联合连续

> example
>
> 多项分布(二项分布的拓展)
>
> 多个离散型随机变量的联合分布

## 独立随机变量

### 定义

随机变量 $X$ 和 $Y$ 称为独立的, 如果对于任意两个实数集 $A$ 和 $B$ , 有
$$
P\set{X\in A,Y\in B}=P\set{X\in A}P\set{Y\in B}
$$
即事件 $E_A=\set{X\in A}$ 和事件 $E_B{Y\in B}$ 独立

对于联合分布函数
$$
F(a,b)=F_X(a)F_Y(b)\quad for\ all\ a\ and\ b
$$
联合连续时, 对联合密度函数
$$
f(x,y)=f_X(x)f_Y(y)\quad for\ all\ x\ and\ y
$$


### 充分必要条件

$$
f_{X,Y}=h(x)g(y)\quad\quad-\infty<x<+\infty, -\infty<y<+\infty
$$

> + 即使两个随机变量不是联合连续的
> + 只要求能分解为两个函数, 不要求两个函数也是密度概率函数

> 注意定义域



## 独立随机变量的和

### 分布及概率密度

$X$ 和 $Y$ 相互独立, 那么
$$
F_{X+Y}(a)=P\set{X+Y\leqslant a}=\iint_{x+y\leqslant a}f_X(x)f_Y(y)dxdy\\
=\int_{-\infty}^{+\infty}\int_{-\infty}^{a-y}f_X(x)f_Y(y)dxdy=\int_{-\infty}^{+\infty}F_X(a-y)f_Y(y)dy
$$
$F_{X+Y}$ 称为分布函数 $F_X$ 和 $F_Y$ 的卷积(convolution), 上式求导有
$$
f_{X+Y}(a)=\int_{-\infty}^{+\infty}f_X(a-y)f_Y(y)dy
$$


### (0,1) 上的均匀分布的随机变量的和

$$
f_X(a)=f_Y(a)=\begin{cases}
1\quad 0<a<1\\
0\quad else
\end{cases}
\\\\
f_{X+Y}=\int_0^1f_X(a-y)dy\\
\\
f_{X+Y}=\begin{cases}
a\quad 0\leqslant a\leqslant 1\\
2-a\quad 1<a<2\\
0\quad else
\end{cases}
$$

也成为"三角分布"



### Gamma 随机变量的和

$\Gamma$ 随机变量的和

#### 回顾

$$
f(x)=\begin{cases}
\frac{\lambda e^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma (\alpha)}\quad x\geqslant 0\\
0\quad x<0
\end{cases}\\
$$

#### 对于给定的 $\lambda$ 在卷积意义下封闭

$X$ 和 $Y$ 分别是参数为 $(s,\lambda)$ 和 $(t,\lambda)$ 的 $\Gamma$ 随机变量, 那么 $X+Y$ 是参数为 $(s+t,\lambda)$ 的 $\Gamma$ 随机变量



#### 正态分布的平方和为卡方分布

如果 $Z_1,Z_2,...,Z_n$ 为相互独立的标准正态随机变量, 那么 $Y=\sum_{i=1}^n Z_i$ 为服从自由度为 $n$ 的卡方分布

 





### 正态随机变量的和

#### 封闭性

如果 $X_i,i=1,2,...,n$ 为独立随机变量, 均服从正态分布, 

各自参数分别为 $(\mu_i,\sigma_i^2),i=1,2,...,n$ ,

那么 $\sum_{i=1}^nX_i$ 服从参数为 $(\sum_{i=1}^n\mu_i,\sum_{i=1}^n\sigma_i^2)$ 的正态分布



### 泊松随机变量的和

随机变量 $X$ 和 $Y$ 服从参数为 $\lambda_1$ 和 $\lambda_2$ 的泊松分布, 那么 $X+Y$ 服从参数为 $\lambda_1+\lambda_2$ 的泊松分布
$$
pf:\\
P\set{X+Y=n}=\sum_{k=1}^nP\set{X=k}P\set{Y=n-k}\\
=\sum_{k=1}^ne^{-\lambda_1}\frac{\lambda_1^k}{k!}e^{-\lambda_2}\frac{\lambda_2^{n-k}}{(n-k)!}=e^{-(\lambda_1+\lambda_2)}\sum_{k=1}^n\frac{\lambda_1^k\lambda_2^{n-k}}{k!(n-k)!}\\
=\frac{e^{-(\lambda_1+\lambda_2)}}{n!}\sum_{k=1}^n\frac{n!\lambda_1^k\lambda_2^{n-k}}{k!(n-k)!}=\frac{e^{-(\lambda_1+\lambda_2)}}{n!}(\lambda_1+\lambda_2)^n
$$


### 二项分布随机变量的和

参数为 $(n,p)$ 和 $(m,p)$ 的二项随机变量 $X$ 和 $Y$ , $X+Y$ 是参数为 $(n+m,p)$ 的二项随机变量



### 几何随机变量的和

#### 回顾

独立重复试验, 每次成功率为 $p,0<p<1$ ,一直进行直到试验成功, $X$ 表示试验总次数

$$
P\set{X=n}=(1-p)^{n-1}p\quad \quad n=1,2,...
$$


#### 求和

$X_1,X_2,...,X_n$ 为参数为 $p_i$ 的几何随机变量, 和 $S_n=\sum_{i=1}^n X_i$ 的分布列为
$$
P\set{S_n=k}=\sum_{i=1}^np^i(1-p_i)^{k-1}\prod_{j\neq i}\frac{p_j}{p_j-p_i}
$$
当所有的 $p_i=p$ 时, 退化为负二项分布

对于有部分概率相同的情况, 使用卷积



## 随机变量的条件分布

### 离散情形下的条件分布

#### 定义

##### 条件分布列

在 $Y=y,P\set{Y=y}>0$ 的条件下定义 $X$ 的分布列
$$
P_{X|Y}\set{x|y}=P\set{X=x|Y=y}=\frac{P\set{X=x|Y=y}}{P\set{Y=y}}=\frac{p(x,y)}{p_Y(y)}
$$

##### 条件分布函数

在 $Y=y,P\set{Y=y}>0$ 的条件下定义 $X$ 的条件分布函数
$$
F_{X|Y}(x|y)=P\set{X\leqslant x|Y=y}=\sum_{a\leqslant x}p_{X|Y}(a|y)
$$

##### 独立

当 $X$ 和 $Y$ 独立时 $\Leftrightarrow$ 条件分布与普通分布相同
$$
P\set{X=x|Y=y}=P\set{X=x}P\set{Y=y}
$$

### 连续情形下的条件分布

#### 定义

$X$ 和 $Y$ 具有联合密度函数 $f(x,y)$ , 在 $Y=y,f_Y(y)>0$ 的条件下定义 $X$ 的条件密度函数
$$
f_{X|Y}(x,y)=\frac{f(x,y)}{f_Y(y)}
$$

#### 含义

$$
f_{X|Y}(x,y)dx=\frac{f(x,y)dxdy}{f_Y(y)dy}\\
=\frac{P\set{x\leqslant X\leqslant x+dx,y\leqslant Y \leqslant y+dy}}{P\set{y\leqslant Y\leqslant y+dy}}
$$

#### 事件条件概率 $\rightarrow$ 条件分布函数

如果 $X$ 和 $Y$ 联合连续, 对于任一几何 $A$ 
$$
P\set{X\in A|Y=y}=\int_Af_{X|Y}(x|y)dx
$$
特别地, 当 $A=(-\infty,a]$ 时,
$$
F_{X|Y}=P\set{X\leqslant a|Y=y}=\int_{-\infty}^af_{X|Y}(x|y)dx
$$


#### 独立

$$
f(x,y)=f_X(x)f_Y(y)
$$

### 离散+连续情形

考虑给定离散随机变量 $N=n$ 条件下 $X$ 的条件分布
$$
\frac{P\set{x<X<x+dx|N=n}}{dx}=\frac{P\set{N=n|x<X<x+dx}}{P\set{N=n}}\frac{P\set{x<X<x+dx}}{dx}\\
\lim\limits_{dx\rightarrow 0}\frac{P\set{x<X<x+dx|N=n}}{dx}=\frac{P\set{N=n|x<X<x+dx}}{P\set{N=n}}f(x)\\
f_{X|N}(x|n)=\frac{P\set{N=n|x<X<x+dx}}{P\set{N=n}}f(x)
$$

### 二元正态分布

## 随机变量函数的联合分布

### 二维定义

设 $X_1,X_2$ 具有联合密度函数 $f_{X_1,X_2}$ 求 $f_{Y_1,Y_2}$ ,其中
$$
y_1=g_1(x_1,x_2)\\
y_2=g_2(x_1,x_2)
$$
由这样的方程组, 可以由 $y$ 唯一确定 $x$ , 即存在唯一的 $h_1,h_2$
$$
x_1=h_1(y_1,y_2)\\
x_2=h_2(y_1,y_2)
$$
同时要求这样的条件

函数 $g_1,g_2$ 对一切 $(x_1,x_2)$ 具有连续偏导数, 并且下列不等式成立
$$
J(x_1,x_2)=\left|
\begin{array}{cccc} 
    \frac{\partial g_1}{\partial x_1}  &  \frac{\partial g_1}{\partial x_2}  \\ 
   \frac{\partial g_2}{\partial x_1}  &  \frac{\partial g_2}{\partial x_2}  
\end{array}
\right| 
=\frac{\partial g_1}{\partial x_1}\frac{\partial g_2}{\partial x_2}-\frac{\partial g_1}{\partial x_2}\frac{\partial g_2}{\partial x_1}\neq 0
$$
那么
$$
f_{Y_1,Y_2}(y_1,y_2)=f_{X_1,X_2}(x_1,x_2)\big|J(x_1,x_2)^{-1}\big|
$$

### 多维情况下

从微积分中类似

## 可交换随机变量

### 连续型随机变量

随机变量序列 $X_1,X_2,...,X_n$ 称为可交换的, 如果对于 $1,2,...,n$ 的每一个排列 $i_1,i_2,...,i_n$ 都有
$$
P\set{X_{i_1}\leqslant x_1,X_{i_2}\leqslant x_2,...,X_{i_n}\leqslant x_n}=P\set{X_1\leqslant x_1,X_2\leqslant x_2,...,X_n\leqslant x_n}
$$
即可交换的随机变量的联合分布与其次序无关

### 离散型

$$
P\set{X_{i_1}= x_1,X_{i_2}= x_2,...,X_{i_n}= x_n}=P\set{X_1= x_1,X_2= x_2,...,X_n= x_n}
$$

### 性质

每一个 $X_i$ 具有相同的概率分布



# 期望的性质

## 随机变量和的期望

$X$ 和 $Y$ 具有二元分布列 $p(x,y)$ , 则
$$
E[g(X,Y)]=\sum_y\sum_xg(x,y)p(x,y)
$$
若 $X$ 和 $Y$ 具有联合分布密度 $f(x,y)$ , 则
$$
E[g(X,Y)]=\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}g(x,y)f(x,y)dxdy
$$

### 引理

对于非负随机变量 $Y$ 
$$
E[Y]=\int_0^{\infty}P\set{Y>y}dy
$$
$pf:$
$$
\int_0^{\infty}P\set{Y>y}dy=\int_0^{\infty}\int_y^{\infty}f_Y(x)dxdy=\int_0^{\infty}f_Y(x)dx\int_0^xdy\\
=\int_0^\infty xf_Y(x)dx=E[Y]
$$

### 证明

$$
E[g(X,Y)]=\int_0^\infty P\set{g(X,Y)>t}dt\\
=\int_0^\infty\bigg( \iint_{(x,y):g(x,y)>t}f(x,y)dydx\bigg)dt\\
=\int_{-\infty}^\infty\int_{-\infty}^\infty \int_{t=0}^{g(x,y)}f(x,y)dtdydx\\
=\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}g(x,y)f(x,y)dxdy
$$

### 线性性

特别地, 对于 $g(X_1,X_2,...,X_n)=\sum X_i$ 
$$
E[X_1+X_2+...+X_n]=E[X_1]+E[X_2]+...+E[X_n]
$$

> P278-P287例题



## 试验序列中事件发生次数的矩

### 事件对出现的次数

对于时间序列 $A_1,A_2,...,A_n$ , 事件发生次数 $X$ , 事件对发生次数 $\tbinom{X}{2}$ , 其中
$$
\tbinom{X}{2}=\sum_{i<j}I_iI_j\\
E[\tbinom{X}{2}]=E[\sum_{i<j}I_iI_j]=\sum_{i<j}P(A_iA_j)\\
E[\frac{X(X-1)}{2}]=\sum_{i<j}P(A_iA_j)\\
E[X^2]-E[X]=2\sum_{i<j}P(A_iA_j)\\
$$

> 可以与 $Var(X)=E[X^2]-E[X]^2$ 联系起来

### k 事件组

$$
E[\tbinom{X}{k}]=\sum_{i_1<i_2<...<i_k}E[I_{i_1}I_{i_2}...I_{i_3}]=\sum_{i_1<i_2<...<i_k}P(A_{i_1}...A_{i_k})
$$

> P288-P293



## 随机变量乘积的期望

### 独立的乘积

若 $X$ 和 $Y$ 相互独立, 则对任何函数 $h$ 和 $g$ , 有
$$
E[g(X)h(Y)]=E[g(X)]E[h(Y)]
$$


### 协方差

#### 定义

$$
Cov(X,Y)=E[(X-E[X])(Y-E[Y])]\\
=E[XY]-E[X]E[Y]
$$

#### 指示两个随机变量的关系

若两个随机变量相互独立, 那么 $Cov(X,Y)=0$ 

> 反之不如此, 即协方差不能作为变量独立的判定依据



#### 性质

$$
\begin{align}
&1.\quad Cov(X,Y)=Cov(Y,X)\\\\
&2.\quad Cov(X,X)=Var(X)\\\\
&3.\quad Cov(aX,Y)=aCov(X,Y)\\\\
&4.\quad Cov\bigg(\sum_{i=1}^nX_i,\sum_{j=1}^nY_j\bigg)=\sum_{i=1}^n\sum_{j=1}^nCov(X_i,Y_j)
\end{align}
$$

由 2 和 4 可以导出
$$
Var(\sum_{i=1}^nX_i)=\sum_{i=1}^nVar(X_i)+2\sum_{i<j}Cov(X_i,X_j)
$$

> P296-P300



## 条件期望

### 离散定义

#### 条件分布列

$$
p_{X|Y}(x|y)=P\set{X=x|Y=y}=\frac{p(x,y)}{p_Y(y)}
$$

#### 条件期望定义

对于 $p_Y(y)>0$ , $X$ 在给定 $Y=y$ 之下的条件期望为
$$
E[X|Y=y]=\sum_xxP\set{X=x|Y=y}=\sum_xxp_{X|Y}(x|y)
$$

### 连续定义

给定 $y\ \ ,f_Y(y)>0$
$$
E[X|Y=y]=\int_{-\infty}^\infty xf_{X|Y}(x|y)dx
$$

### 条件期望满足期望的性质

正如条件概率满足概率的所有性质, 条件期望也满足期望的所有性质.

事实上, 给定 $Y=y$ 之下的条件期望可以看成是较小样本空间中的普通期望, 这个小的样本空间由满足条件 $\set{Y=y}$ 的所有样本点组成



### 利用条件计算期望

用 $E[X|Y]$ 表示随机变量 $Y$ 的函数, 它在 $Y=y$ 处的值为 $E[X|Y=y]$ , 注意到 $E[X|Y]$ 是一个随机变量, 我们有
$$
E[X]=E\bigg[E[X|Y]\bigg]
$$

> P303-P310



### 用条件计算概率

对于随机事件 $E$ , $X$ 为其示性函数
$$
X=\begin{cases}
1\quad E\ happens\\
0\quad else
\end{cases}
$$
有
$$
E[X]=P(E)\\
E[X|Y=y]=P(E|Y=y)\quad for\ any\ Y
$$
$\Rightarrow$

离散情况下
$$
P(E)=\sum_yP(E|Y=y)P(Y=y)
$$
连续情况下
$$
P(E)=\int_{-\infty}^\infty P(E|Y=y)f_Y(y)dy
$$

> 全概公式

> P311-P313



### 条件方差

#### 定义

$$
\begin{align}
Var(X|Y)&=E\bigg[\big(X-E[X|Y]\big)^2\bigg|Y\bigg]\\
&=E[X^2|Y]-(E[X|Y])^2
\end{align}
$$

#### 条件方差公式

$$
Var(X)=E[Var(X|Y)]+Var(E[X|Y])
$$

> P314 315



### 条件期望及预测

观测值 $X$ , 希望有函数 $g$ , 预测 $Y$ , 即用 $g(X)\approx Y$

#### 最好的预测值

最好的预测值为 $g(X)=E[Y|X]$

##### 依据

$$
E[(Y-g(X))^2]\geqslant E[(Y-E[Y|X])^2]
$$

> pf?

> P316-P319



## 矩母函数

### 定义

随机变量 $X$ 的矩母函数 $M(t)$ 
$$
M(t)=E[e^{tX}]=\begin{cases}
\sum_xe^{tx}p(x)\quad 离散\\\\
\int_{-\infty}^\infty e^{tx}f(x)dx\quad 连续
\end{cases}
$$
$t\in \R$ , $X$ 的所有阶矩都可以从 $M(t)$ 在 $t=0$ 的各阶微商得到
$$
M^{(n)}(t)=E[X^ne^{tX}]\quad n\geqslant 1\\
M^{(n)}(0)=E[X^n]
$$

> 一些计算 P320-P325



## 联合矩母函数

暂略

## 正态随机变量进一步的性质

暂略

## 期望的一般定义

暂略





# 极限定理

> 例题从P354开始

## 弱大数律

### 马尔可夫不等式

$X$ 为取非负值得随机变量, 对于任何常数 $a>0$ , 有
$$
P\set{X\geqslant a}\leqslant \frac{E[X]}{a}
$$

> pf



### 切比雪夫不等式

$X$ 是一随机变量, 期望 $\mu$ , 方差 $\sigma^2$ ,对于任意 $k>0$
$$
P\set{|X-\mu|\geqslant k}\leqslant \frac{\sigma^2}{k^2}
$$

> pf



### 方差为0的充要条件

$$
Var(X)=0\quad\Leftrightarrow\quad P\set{X=E[X]}=1
$$

> pf



### 弱大数律

$X_1,X_2,...$ 为独立同分布的随机变量序列, 其公共期望 $E[X_i]=\mu$ 为有限, 则对任何 $\varepsilon>0$
$$
P\set{\bigg|\frac{X_1+X_2+...+X_n}{n}-\mu\bigg|\geqslant \varepsilon}\rightarrow 0\quad n\rightarrow \infty
$$




## 中心极限定理

大量的独立随机变量之和的分布近似为正态分布

### 叙述

$X_1,X_2,...$ 为独立同分布序列, 其公共分布的期望为 $\mu$ ,方差为 $\sigma^2$ , 则随机变量 $\frac{X_1+...+X_n-n\mu}{\sigma \sqrt{n}}$ 的分布在 $n\rightarrow \infty$ 时趋向于标准正态分布, 即对任何 $a\in (-\infty,\infty)$
$$
P\set{\frac{X_1+...+X_n-n\mu}{\sigma \sqrt{n}}\leqslant a}\rightarrow \frac{1}{\sqrt{2\pi}}\int_{-\infty}^ae^{-x^2/2}dx\quad n\rightarrow \infty
$$


### 引理

暂略

### 相互独立时

暂略



## 强大数律

独立同分布随机变量序列, 前 $n$ 个观察值的平均值以概率 1 地收敛到分布的平均值

### 定理

$X_1,X_2,...$ 为独立同分布序列, 其公共分布的期望为 $\mu$ 有限
$$
\frac{X_1+X_2+...+X_n}{n}\rightarrow \mu\quad n\rightarrow \infty
$$
以概率为 1 地成立

