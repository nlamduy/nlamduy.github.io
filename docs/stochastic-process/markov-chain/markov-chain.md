---
layout: default
math: mathjax
title: Markov Chain
parent: Stochastic Process
# has_children: true
nav_order: 4
---

# Markov Chain
{: .no_toc }

Xích Markov là một hệ thống toán học diễn ra các chuyển đổi từ trạng thái này sang trạng thái khác, trong một số lượng hữu hạn hoặc đếm được các trạng thái có thể. Đây là một quá trình ngẫu nhiên nơi trạng thái tương lai chỉ phụ thuộc vào trạng thái hiện tại và không phụ thuộc vào chuỗi các sự kiện đã xảy ra trước đó. Tính chất này được gọi là **“không nhớ” và là một đặc điểm chính của chuỗi Markov**.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


# Stochastic process

Một quá trình ngẫu nhiên là họ của biến ngẫu nhiên $$\{X_t : t \in T\}$$ nhận giá trị trong không gian trạng thái, trong đó:

{: .highlight}
- Cho mỗi $$t \in T, X_t$$ là một biến ngẫu nhiên.
- Chỉ số $$T$$ và không gian trạng thái có thể là liên tục hoặc rời rạc.
- Cho $$T = \{0,1,2,3,4,...,\}$$ (rời rạc) hoặc $$T = \mathbb{R}, \mathbb{R^+}, \mathbb{R^2}, \mathbb{R^3}$$ (liên tục).

![markov_eg2](/assets/img/stochastic-process/markov_eg2.png)

Một số ví dụ:

- Thời gian, trạng thái rời rạc: Xích Markov
- Thời gian rời rạc, trạng thái liên tục: Kalma Filter
- Thời gian liên tục, trạng thái rời rạc: Birth and Death Process
- Thời gian, trạng thái liên tục: Brownian Motion

# Markov assumption

**Đặt vấn đề:** Cho X là một quá trình ngẫu nhiên rời rạc với $$t = \{0, 1, ..., n\}$$ với $$n$$ là thời điểm hiện tại. Giá trị của biến ngẫu nhiên trong quá khứ $$X_0, ..., X_{n - 1}$$ và hiện tại $$X_n$$ cho chúng ta biết gì về phân phối của $$X_{n + 1}$$?

![markov_eg3](/assets/img/stochastic-process/markov_eg3.png)

{: .highlight }
**Những gì xảy ra trong tương lai chỉ phụ thuộc vào hiện tại:**
$$
P\{X_{n + 1} = j \vert X_n = i, X_{n - 1} = a\} = P\{X_{n + 1} = j \vert X_n = i\}
$$

# References

Nguyen Huu, Thai (n.d.). Lecture: Conditional Probability and Conditional Expectation. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

