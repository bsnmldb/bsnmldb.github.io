---
title: A Concise Introduction to Probability Theory
author: yiwei
date: '2023-11-29 00:00:00 +0800'
categories: [Mathematics]
tags: [probability theory, notes]
pin: false
math: true
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


### 推广3(无限个事件)

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

  

