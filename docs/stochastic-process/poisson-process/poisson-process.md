---
layout: default
math: mathjax
title: Poisson Process
parent: Stochastic Process
nav_order: 5
---

# Poisson Process
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Counting process

Một quá trình ngẫu nhiên $$\{N(t), t \ge 0\}$$ được gọi là một **quá trình đếm** nếu $$N(t)$$ đại diện cho tổng số [biến cố](https://nlamduy.github.io/docs/stochastic-process/probability-theory/sample-space-events.html#events) xảy ra trong thời gian $$t$$.

Ví dụ: 

Xem xét quá trình [Bernoulli](https://nlamduy.github.io/docs/stochastic-process/random-variables/discrete-random-variable.html#bernoulli-and-binomial-random-variable) sau:

Tung một đồng xu trong 8 ngày và biến cố thành công là mặt ngửa (1). Giả sử kết quả tung đồng xu mỗi ngày là 00101011. Quá trình đếm $$N(t)$$ được mô tả bằng 00112234.

{: .note-title }
> Một số tính chất của quá trình đếm
>
> Cho một quá trình đếm $$\{ N(t), t \ge 0 \}$$ thoả mãn:
>
> 1. $$N(t) > 0$$ với mọi $$t \ge 0$$
> 2. $$N(t)$$ nhận giá trị nguyên (integer values)
> 3. Nếu $$s < t$$ thì $$N(s) < N(t)$$
> 4. Cho $$s < t, N(t) - N(s)$$ bằng số lượng biến cố xảy ra trong nửa khoảng $$(s, t]$$

![poisson_eg1](/assets/img/stochastic-process/poisson_eg1.png)

Một quá trình đếm có **có số gia độc lập** (independent increment) nếu: số biến cố xảy ra trong khoảng thời gian từ 0 đến s không liên quan đến số biến cố xảy ra trong khoảng thời gian từ s đến t, $$N(s) \perp N(t) - N(s)$$. Nói cách khác số biến cố trong một khoảng thời gian là độc lập với khoảng thời gian khác.

# Poisson process

{: .note }
> Một quá trình đếm $$\{N(t), t \ge 0\}$$ được gọi là quá trình Poisson với tốc độ (rate) $$\lambda > 0$$ nếu các tiên đề sau đúng:
> 1. Giá trị xuất phát tại $$N(0) = 0$$.
> 2. Tính độc lập (independence): $$N$$ có tính chất số gia độc lập. Chẳng hạn, số lượng biến cố xảy ra tại các khoảng thời gian không giao nhau (disjoint time) là độc lập.
> 3. Tính thuần nhất (homogeneity): Phân phối xác suất của số lượng biến cố trong một khoảng thời gian chỉ phụ thuộc vào độ dài của khoảng thời gian đó, $$P(N(t + h) - N(t) = 1) = \lambda h + o(h)$$. Nói cách khác, nếu cho một khoảng thời gian (time duration) xác định, thì xác suất xảy ra $$k$$ sự kiện là như nhau dù khoảng này nằm ở thời điểm nào.
> 4. Tính không đồng thời (non-concurrence): Xác suất để ít nhất hai biến cố xảy ra đồng thời tại một điểm  có độ dài $$h$$ là rất nhỏ, $$P(N(t + h) - N(t) \ge 2) = o(h)$$.
>
> *trong đó, $$o(h)$$ là $$lim_{h \to 0}\frac{f(h)}{h} = 0$$*.

Từ những tiên đề này có thể suy ra một tính chất quan trọng, đó là có thể **đặt lại quá trình đếm**. Giả sử chúng ta chỉ quan tâm tới đoạn [s, s+t] như bên dưới, thì có thể bỏ qua quá trình đếm đoạn [0, s].

![poisson_eg2](/assets/img/stochastic-process/poisson_eg2.png)

# References

MIT OpenCourseWare. (n.d.). L22.2 Definition of the Poisson Process \[Video\]. YouTube. https://www.youtube.com/watch?v=D_EGYzqmapc

Nguyen Huu, Thai (n.d.). Lecture: Poisson Process. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

