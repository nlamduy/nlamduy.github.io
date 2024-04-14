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
- Chỉ số $$T$$ và không gian trạng thái (state space) có thể là liên tục hoặc rời rạc.
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

# Transition probability matrix

Nếu $$P(X_{n + 1} = j \vert X_n = i) = P_{ij}$$ không phụ thuộc vào $$n$$ thì quá trình $$X_n : n = 0, 1, 2, ...$$ được gọi là xích Markov dừng (stationary). Trong đó, $$P_{ij}$$ được gọi là xác suất chuyển (transition probabilities) từ trạng thái $$i$$ sang trạng thái $$j$$.

Ma trận xác suất chuyển:

$$
P = \begin{bmatrix}
P_{00} & P_{01} & P_{02} & ... & P_{0j} & ... \\
P_{10} & P_{11} & P_{12} & ... & P_{1j} & ... \\
... & ... & ... & ... & ... & ... \\
P_{i0} & P_{i1} & P_{i2} & ... & P_{ij} & ... \\
... & ... & ... & ... & ... & ... 
\end{bmatrix}
$$

Xác suất chuyển $$P_{ij}$$ thoả mãn những điều sau:
- Xác suất chuyển không âm $$P_{ij} \ge 0$$ cho mọi $$i, j$$.
- Tổng xác suất (theo dòng) $$\sum_j P_{ij} = 1$$ cho mọi $$i$$.

**Quy tắc đọc là dòng sang cột.**

Ví dụ 1:

Cho xích Markov $$\{X_0, X_1, X_2, ..., X_n, X_{n + 1} \}$$ mô tả thời tiết với 3 trạng thái $$S = \{Sunny, Cloudy, Rainny\}$$ và xác suất chuyển như sau:

![markov_eg4](/assets/img/stochastic-process/markov_eg4.png)

Xác định xác suất chuyển từ trạng thái Sunny sang Sunny, Sunny sang Rainny, Rainny sang Cloudy, Rainny sang Sunny.

Đáp án:

- $$P\{X_{n + 1} = Sunny \vert X_n = Sunny\} = 0.2$$
- $$P\{X_{n + 1} = Rainny \vert X_n = Sunny\} = 0.4$$
- $$P\{X_{n + 1} = Cloudy \vert X_n = Rainny\} = 0.7$$
- $$P\{X_{n + 1} = Sunny \vert X_n = Rainny\} = 0.0$$

Diễn đạt bằng lời như sau: Giả sử $$n$$ là ngày hôm nay thì, xác suất ngày hôm nay ($$X_n$$) là Sunny và ngay mai ($$X_{n + 1}$$) tiếp tục Sunny là 0.2. Hoặc, xác suất ngày hôm nay ($$X_n$$) là Sunny và ngay mai ($$X_{n + 1}$$) Rainny là 0.2. Lưu ý, đọc từ dòng (đại diện cho trạng thái thời điểm hiện tại) sang cột (đại diện cho trạng thái ở tương lai).

Ngoài ra, còn có thể biểu diễn ma trận xác suất chuyển bằng đồ thị bên dưới:

![markov_eg5](/assets/img/stochastic-process/markov_eg5.png)

Ví dụ 2:

Cho xích Markov $$\{X_0, X_1, ...\}$$ gồm 3 trạng thái $$S = \{0, 1, 2\}$$ với ma trận xác suất chuyển:

![markov_eg6](/assets/img/stochastic-process/markov_eg6.png)

và xác suất phân phối khởi đầu (xuất phát của xích Markov) $$P(X_0 = 0) = 0.3, P(X_0 = 1) = 0.4$$, hoặc $$P(X_0 = 2) = 0.3$$. Nói cách khác ở thời điểm bắt đầu ($$t = 0$$), X có thể nhận 1 trong 3 trạng thái với xác suất tương ứng như trên. 

![markov_eg7](/assets/img/stochastic-process/markov_eg7.png)

Tính:

1. $$P(X_0 = 0, X_1 = 2, X_2 = 2)$$
2. $$P(X_1 = 1, X_2 = 1 \vert X_0 = 0)$$

Đáp án:

Để tính được các xác suất trên, cần sử dụng [xác suất có điều kiện](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities).

1. Tính $$P(X_0 = 0, X_1 = 2, X_2 = 2)$$:

$$
\begin{aligned}
& P(X_0 = 0, X_1 = 2, X_2 = 2) \\
& = P(X_2 = 2 | X_0 = 0, X_1 = 1)P(X_0 = 0, X_1 = 1) \\
& = P(X_2 = 2 | X_1 = 1)P(X_1 = 1 | X_0 = 0)P(X_0 = 0) \\
& = 0 \cdot 0.2 \cdot 0.3 = 0
\end{aligned}
$$

Ở đây, $$P(X_2 = 2 \vert X_0 = 0, X_1 = 1)$$ có thể bằng $$P(X_2 = 2 \vert X_1 = 1)$$ vì giả định của xích Markov là những gì xảy ra ở tương lai ($$X_2$$) chỉ phụ thuộc vào hiện tại ($$X_1$$), nên ta có thể bỏ qua quá khứ $$X_0$$ trong trường hợp này.

2. Tính $$P(X_1 = 1, X_2 = 1 \vert X_0 = 0)$$:

$$
\begin{aligned}
& P(X_1 = 1, X_2 = 1 | X_0 = 0) \\
& = P(X_2 = 1 | X_1 = 1, X_0 = 0)P(X_1 = 1 | X_0 = 0) \\
& = P(X_2 = 1| X_1 = 1)P(X_1 = 1 | X_0 = 0) \\
& = 0.1 \cdot 0.2 = 0.02
\end{aligned}
$$

Từ ví dụ này, **ta có thể mở rộng thêm phần xác suất có điều kiện** cho xích Markov:

{: .highlight}
$$
\begin{aligned}
P(A,B|C) & = \frac{P(A,B,C)}{P(C)} \\
& = \frac{P(A|B,C)P(B,C)}{P(C)} \\
& = P(A|B,C)P(B|C) \\
& = P(A,B|C) = P(A|B,C)P(B|C)
\end{aligned}
$$

# References

Nguyen Huu, Thai (n.d.). Lecture: Conditional Probability and Conditional Expectation. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

