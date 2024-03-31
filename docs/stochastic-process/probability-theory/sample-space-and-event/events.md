---
layout: default
math: mathjax
title: Sample Space and Events
parent: Probability Theory
grand_parent: Stochastic Process
nav_order: 1
---

# Navigation Structure
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Sample Space

Không gian mẫu (sample space) là **tập hợp tất cả kết quả có thể xảy ra** của một thí nghiệm (experiment), được ký hiệu là $$\Omega$$. Xác suất $$P(\Omega) = 1$$.

**Mỗi kết quả trong không gian mẫu là một điểm mẫu** (sample point).

Ví dụ, xác định không gian mẫu:

- Tung một đồng xu? $$\Rightarrow \Omega = \{H,T\}$$
- Đổ một con xúc xắc? $$\Rightarrow \Omega = \{1,2,3,4,5,6\}$$
- Đổ hai con xúc xắc? $$\Rightarrow \Omega = \{(1,1), (1,2), (1,3), ..., (6,6)\}$$

# Events

Biến cố (events) là một **tập con của không gian mẫu** $$\Omega$$, được ký hiệu $$E \subseteq \Omega$$.

Ví dụ, biến cố mặt xúc xắc là chẵn: $$E = \{2, 4, 6\}$$.

## Complement of an event

Phần bù của một biến cố E là tập hợp các **điểm mẫu thuộc không gian mẫu** $$\Omega$$ nhưng **không thuộc biến cố E**, được kí hiệu $$E^c$$.


**Xác suất phần bù** của biến cố E:

{: .highlight }
$$
P(E^c) = 1 - P(E)
$$

Ví dụ:

Gọi E là biến cố mặt xúc xắc chẵn. Tính xác suất phần bù $$E^c$$.

Ta biết không gian mẫu $$\Omega = \{1, 2, 3, 4, 5, 6\}$$, biến cố $$E = \{2, 4, 6\}$$, $$P(E) = \frac{3}{6}$$. Do đó $$P(E^c) = 1 - \frac{3}{6} = \frac{1}{2}$$


## Union of two events

Hợp của hai biến cố $$E_1$$ và $$E_2$$ là tập hợp **tất cả điểm mẫu thuộc** $$E_1$$ **hoặc** $$E_2$$ **hoặc cả hai**, được ký hiệu $$E_1 \cup E_2$$.

Ví dụ, xác định hợp của biến cố $$E_1 = \{1,2,3\}$$ và $$E_2 = \{3,4\}$$: $$E_1 \cup E_2 = \{1,2,3,4\}$$


## Intersection of two events

Giao của hai biến cố $$E_1$$ và $$E_2$$ là tập hợp **điểm mẫu thuộc cả** $$E_1$$ **và** $$E_2$$, được ký hiệu $$E_1 \cap E_2$$.

Ví dụ, xác định giao của biến cố $$E_1 = \{1,2,3\}$$ và $$E_2 = \{3,4\}$$: $$E_1 \cap E_2 = \{3\}$$


## Mutually exclusive events

Hai biến cố xung khắc nếu không có điểm mẫu chung nào, hay $$E_1 \cap E_2 = \emptyset$$. Xác suất của $$P(E_1 \cap E_2) = 0$$.


## Collectively exhaustive events

**Các biến cố xung khắc và đẩy đủ nếu thoả những điều kiện sau:**

1. Không có điểm mẫu chung nào, $$E_1 \cap E_2 = \emptyset$$, $$P(E_1 \cap E_2) = 0$$.
2. Tập hợp điểm mẫu của tất cả biến cố chính bằng không gian mẫu $$\Omega$$, $$E_1 \cup E_2 = \Omega$$.
3. Một trong các biến cố nhất định phải xảy ra, $$P(E_1 \cup E_2) = 1$$.

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Nguyen Huu, Thai. (n.d.). Lecture: Introduction to Probability Theory. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.