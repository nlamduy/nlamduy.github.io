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

# Properties of Poisson process

Một số tính chất của quá trình Poisson:

{: .note-title }
> Phân phối của thời gian chờ để xảy ra biến cố đầu tiên
>
> Nếu $$T_1$$ là thời gian chờ cho đến khi biến cố đầu tiên xảy ra của một quá trình Poisson $$\{N(t), t \ge 0\}$$ với tham số $$\lambda$$ thì: $$P(T_1 > t) = P(N(t) = 0) = e^{-\lambda t}$$.

{: .note-title }
> Thời gian chờ giữa các biến cố xảy ra liên tục (interarrival times)
>
> Cho biến ngẫu $$T_n, n = 1, 2, ...$$ là thời gian giữa biến cố thứ $$(n - 1)^{st}$$ và $$n^{th}$$ trong một quá trình Poisson $$\{N(t), t \ge 0\}$$ với tham số $$\lambda$$, thì $$T_1, T_2, ...$$ là độc lập và có cùng phân phối mũ với tham số $$\lambda$$.

![poisson_eg3](/assets/img/stochastic-process/poisson_eg3.png)

Trong đó, $$S_n$$ là thời điểm mà biến cố thứ $$n$$ xảy ra. Cụ thể, $$S_1 = T_1, S_2 = T_1 + T_2, S_3 = T_1 + T_2 + T_3$$ và $$S_2, S_3$$ có [phân phối gamma](https://nlamduy.github.io/docs/stochastic-process/random-variables/continuous-random-variable.html#gamma-random-variable) với:

$$
f(t) = \lambda e^{-\lambda t}\frac{(\lambda t)^{n - 1}}{(n - 1)!} \text{ , } t > 0
$$

Ví dụ: Tính $$S_2$$.

$$
f_{S_2} = \lambda e^{-\lambda t} \frac{(\lambda t)^{2-1}}{(2-1)!}
$$

{: .note-title }
> Phân phối của quá trình Poisson
>
> Cho một quá trình Poisson $$\{N(t), t \ge 0\}$$ với tham số $$\lambda$$, $$N(t)$$ là một biến ngẫu nhiên có phân phối Poisson với tham số $$\lambda t$$. Trong đó, $$t$$ là độ dài đoạn thời gian chúng ta quan tâm và $$\lambda$$ là tốc độ (rate) luôn luôn cố định.

![poisson_eg4](/assets/img/stochastic-process/poisson_eg4.png)

*Lưu ý là chúng ta không biết có bao nhiêu biến cố xảy ra trong đoạn [0, t] mà chỉ biến phân phối trong đoạn này.*

Ví dụ:

![poisson_eg5](/assets/img/stochastic-process/poisson_eg5.png)

- $$N(1)$$: là số biến cố xảy ra trong đoạn [0, 1] có phân phối $$N(1) \sim Pois(\lambda \cdot 1)$$.
- $$N(3)$$: là số biến cố xảy ra trong đoạn [0, 3] có phân phối $$N(1) \sim Pois(\lambda \cdot 3)$$.
- $$N(3) - N(1)$$: là số biến cố xảy ra trong nửa khoảng (1, 3] có phân phối $$N(1) \sim Pois(\lambda \cdot (3 - 1))$$.

# References

MIT OpenCourseWare. (n.d.). L22.2 Definition of the Poisson Process \[Video\]. YouTube. https://www.youtube.com/watch?v=D_EGYzqmapc

Nguyen Huu, Thai (n.d.). Lecture: Poisson Process. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

