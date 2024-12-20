---
title: 'Understanding Perplexity in NLP'
date: 2024-06-25
permalink: /posts/2024/06/perplexity/
tags:
  - natural language processing
  - perplexity
---

When trying to understand the relationship between perplexity and entropy, I searched through many resources on the Internet, but none provided a detailed formula derivation and understanding. Therefore, I have written this article to document my thoughts.

# Perplexity

在介绍困惑度（perplexity）之前，我们需要先理解什么是语言模型（language model）。语言模型是`根据前文预测下一个词(token)`的概率模型，即给定前文$w_1w_2\dots w_t$，建模$P(w_{t+1}\mid w_1w_2\dots w_t)$。根据概率的链式法则，$P(w_1w_2\dots w_n)=P(w_1)P(w_2\mid w_1)\dots P(w_n\mid w_1w_2\dots w_{n-1})$，所以语言模型也可以等价描述为`预测一个句子出现的概率`。

困惑度的定义为：
$$
\text{perplexity}(w_1w_2\dots w_n)=\frac{1}{\sqrt[n]{P(w_1w_2\dots w_n)}}
$$
它用于描述某个语言模型$P(\cdot)$对于某个句子$s=w_1w_2\dots w_n$出现的困惑程度，即语言模型认为该句子出现的概率越大，就越不应该感到困惑；反之语言模型认为该句子出现的概率越小，对于该句子的出现就越应该感到困惑。

困惑度的最小值为1，但没有最大值，可以趋近于无穷大。

由于句子越长，语言模型预测该句子出现的概率往往越小，这可以从两个角度理解：

\1. 句子越长，在相同词表大小下，句子的数量就越多，每个句子平均下来的概率自然越小。
\2. 考虑最简单的模型，每个词之间没有关联，即$P(w_1w_2\dots w_n)=P(w_1)P(w_2)\dots P(w_n)$，那么因为$\forall w,P(w)\leq 1$，所以随着句子长度的增加，句子出现的概率必然越来越小。

上面 $n$ 次根式是为了对句子长度做归一化，以获得更合理的perplexity进行评价。

在实践中，通常使用测试集的句子计算模型的困惑度作为模型的评价指标。这是因为测试集的句子本身是合理的、已出现过的，好的模型对于这些正确的、好的句子不应该感到困惑。

# Entropy

未完待续...

