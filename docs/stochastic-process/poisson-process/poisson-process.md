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

{: .note-title}
> Quá trình Poisson thuần nhất (homogenous)
>
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

Ví dụ 1: Tính $$S_2$$.

$$
f_{S_2} = \lambda e^{-\lambda t} \frac{(\lambda t)^{2-1}}{(2-1)!}
$$

{: .note-title }
> Phân phối của quá trình Poisson
>
> Cho một quá trình Poisson $$\{N(t), t \ge 0\}$$ với tham số $$\lambda$$, $$N(t)$$ là một biến ngẫu nhiên có phân phối Poisson với tham số $$\lambda t$$. Trong đó, $$t$$ là độ dài đoạn thời gian chúng ta quan tâm và $$\lambda$$ là tốc độ (rate) luôn luôn cố định.

![poisson_eg4](/assets/img/stochastic-process/poisson_eg4.png)

*Lưu ý là chúng ta không biết có bao nhiêu biến cố xảy ra trong đoạn [0, t] mà chỉ biến phân phối trong đoạn này.*

Ví dụ 2:

![poisson_eg5](/assets/img/stochastic-process/poisson_eg5.png)

- $$N(1)$$: là số biến cố xảy ra trong đoạn [0, 1] có phân phối $$N(1) \sim Pois(\lambda \cdot 1)$$.
- $$N(3)$$: là số biến cố xảy ra trong đoạn [0, 3] có phân phối $$N(1) \sim Pois(\lambda \cdot 3)$$.
- $$N(3) - N(1)$$: là số biến cố xảy ra trong nửa khoảng (1, 3] có phân phối $$N(1) \sim Pois(\lambda \cdot (3 - 1))$$.

Ở mục thứ 3, có một số điểm cần làm rõ như sau:
- Chúng ta chỉ quan tâm để những gì xảy ra **sau thời điểm 1** đến hết thời điểm 3.
- Khoảng (1, 3] là **số biến cố** xảy ra trong khoảng thời gian này, khác với thời gian chờ giữa 2 hay nhiều biến cố xảy ra liên tiếp. Do đó khoảng (1, 3] trong trường hợp này có phân phối Poisson thay vì Gamma.
- Quá trình Poisson cũng có tính chất của [quá trình Markov](https://nlamduy.github.io/docs/stochastic-process/markov-chain/markov-chain.html#markov-assumption), đó là tính không nhớ. Nên chúng ta có thể bỏ qua những gì đã xảy ra ở đoạn [0 , 1].

Ví dụ 3:

Giả sử số lượng cuộc gọi đến một tổng đài là một quá trình Poisson với tham số $$\lambda = 30$$ / giờ. Tính xác suất không có cuộc gọi nào đến trong 5 phút tiếp theo? Trung bình có bao nhiêu cuộc gọi trong 10 phút?

Đáp án:

Xác suất không có cuộc gọi nào trong 5 phút tiếp theo:

- Gọi biến ngẫu nhiên $$N(t)$$ là số cuộc gọi đến tổng đài trong đoạn [0, t].
- Phân phối của $$N(t) \sim Pois(\lambda \cdot t) \Leftrightarrow N(\frac{5}{60}) \sim Pois(30 \cdot \frac{5}{60})$$.

$$
P\{N(\frac{1}{12}) = 0\} = e^{-5/2} \cdot \frac{(5/2)^0}{0!} \approx 0.082
$$

*Xem lại phần [Phân phối Poisson](https://nlamduy.github.io/docs/stochastic-process/random-variables/discrete-random-variable.html#poisson-random-variable).*

{: .warning-title}
> Nhắc lại
>
> Trong **quá trình Poisson**, $$P\{ X = i\} = e^{-\mu} \cdot \frac{(\mu)^i}{i!}$$, với $$\mu = \lambda t$$.

Số cuộc gọi trung bình trong 10 phút:

- Phân phối của $$N(\frac{10}{60}) \sim Pois(30 \cdot \frac{10}{60})$$.
- Kỳ vọng của phân phối poisson: $$E[N] = \lambda$$.

$$
E[N(\frac{1}{6})] = E[Pois(30 \cdot \frac{10}{60})] = 5
$$

*Xem lại phần [Giá trị kỳ vọng cho phân phối Poisson](https://nlamduy.github.io/docs/stochastic-process/random-variables/expectation-variance.html#discrete-random-variable).*

Ví dụ 4:

Cho $$N(t)$$ là số lượng khách hàng đến một cửa hàng là một quá trình Poisson với tham số $$\lambda = 2$$ khách hàng / giờ. Tính các xác suất và kỳ vọng sau:

a. $$P\{N(1) = 2\}$$

b. $$P\{N(1) = 2, N(3) = 6\}$$

c. $$P\{N(1) = 2 \vert N(3) = 6\}$$

d. $$P\{N(3) = 6 \vert N(1) = 2\}$$

e. $$E[N(2)], E[(N(1))^2], E[N(1)N(2)]$$

Đáp án:

a. $$P\{N(1) = 2\} = e^{-\lambda} \cdot \frac{\lambda^2}{2!} \approx 0.2707 $$

b. 

$$
\begin{aligned}
P\{N(1) = 2, N(3) = 6\} & = P\{N(1) = 2, N(3) - N(1) = 4\} \\
& = P\{N(1) = 2\}P\{N(3) - N(1) = 4\} \\
& = 0.2707 \cdot e^{-2\lambda} \cdot \frac{(2\lambda)^4}{4!} \\
& \approx 0.0528
\end{aligned}
$$

c.

$$
\begin{aligned}
P\{N(1) = 2 \vert N(3) = 6\} & = \frac{P\{N(1) = 2, N(3) = 6\}}{P\{N(3) = 6\}} \\
& = \frac{0.0528}{e^{-3\lambda} \frac{(-3\lambda)^6}{6!}} \\
& \approx 0.3287
\end{aligned}
$$

e.

$$E[N(2)] = 2\lambda = 4$$.

$$E[(N(1))^2] = (1\lambda)^2 + 1\lambda = 6$$.

$$
\begin{aligned}
E[N(1)N(2)] & = E[N(1) \cdot (N(2) - N(1))] \\
& = E[N(1)] \cdot E[N(2) - N(1)] = \lambda \cdot \lambda = \lambda^2 \\
& \Leftrightarrow E[N(1)N(2)] - E[N^2(1)] = \lambda^2 \\
\Leftrightarrow E[N(1)N(2)] & = \lambda^2 + E[N^2(1)] \\
\Leftrightarrow E[N(1)N(2)] & = \lambda^2 + \lambda^2 + \lambda = 2\lambda^2 + \lambda
\end{aligned}
$$

{: .new }
> Nếu biến ngẫu nhiên $$X \sim Pois(\mu)$$:
>
> - $$E[X] = \mu$$.
> - $$E[X^2] = \mu^2 + \mu$$.
> - $$Var[X] = \mu$$.
>
> *Trong đó $$\mu = \lambda \cdot t$$, với $$t$$ là độ dài thời gian quan tâm*.

{: .note-title}
> Biến cố khác nhau trong quá trình Poisson
>
> Cho một quá trình Poisson $$\{N(T), t \ge 0 \}$$ với tham số $$\lambda$$ và mỗi thời điểm có một biến cố xảy ra, được định nghĩa Loại 1 với xác suất $$p$$ và Loại 2 với xác suất $$1 - p$$. Cho $$N_1(t), N_2(t)$$ là số biến cố Loại 1, Loại 2 xảy ra trong khoảng thời gian $$[0, t]$$. Khi đó, $$\{N_1(t), t \ge 0\}$$ và $$\{ N_2(t), t \ge 0 \}$$ là hai quá trình Poisson với tham số lần lượt là $$\lambda_1, \lambda_2$$.

Ví dụ 5:

Nếu người nhập cư đến khu A có phân phối Poisson với tốc độ (rate) 10 người / tuần, và xác suất người nhập cư nói tốt tiếng anh là 1/12, thì xác suất không người nhập cư nào nói tốt tiếng anh khi đến khu A vào tháng 2 là bao nhiêu?

Đáp án:

Gọi $$N_1(t)$$ là số người nhập cư nói tiếng anh tốt tại $$t$$ với xác suất $$p = \frac{1}{2}$$, $$N_2(t)$$ là số người nhập cư không nói tiếng anh tại $$t$$ với xác suất $$(1- p) = \frac{11}{12}$$, có tham số lần lượt là $$\lambda_1 = \lambda p = 10 \cdot \frac{1}{12} = \frac{5}{6}$$, $$\lambda_2 = \lambda (1-p) = 10 \cdot \frac{11}{12} = \frac{55}{6}$$.

Xác suất không có người nói tốt tiếng anh trong tháng 2 là $$P\{N_1(4) = 0\}$$. Trong đó, $$t=4$$ do đơn vị tính đang là người / tuần và $$N_1(4) \sim Pois(10 \cdot \frac{1}{12} \cdot 4 = \frac{10}{3})$$.

$$P\{N_1(4) = 0\} = e^{-\mu} \cdot \frac{(\mu)^i}{i!} = e^{-10/3} \cdot \frac{(10/3)^0}{0!}$$

{: .warning-title}
> Lưu ý
>
> Trong trường hợp này, $$\mu = \lambda p t$$, do có thêm xác suất $$p$$ để biến cố xảy ra.

Ví dụ 6:

Một công ty bảo hiểm có hai loại đền bù. Cho $$N_i(t)$$ là số đền bù lại $$i$$ tại thời điểm $$t$$, $$N\{N_1(t), t \ge 0\}$$ và $$N\{N_2(t), t \ge 0\}$$ là hai quá trình Poisson độc lập với tham số lần lượt $$\lambda_1 = 10, \lambda_2 = 1$$. Trong đó, số tiền yêu cầu đền bù loại 1 và loại 2 tuân theo phân phối mũ với trung bình lần lượt là $$\mu_1 = 1000, \mu_2 = 5000$$. Một yêu cầu đền bù lớn hơn bằng $4000 vừa xuất hiện, xác suất đây là đền bù loại 1 là bao nhiêu?

Đáp án:

- $$\lambda_1 = \lambda p = 10$$.

- $$\lambda_2 = \lambda (1-p) = 1$$.

Ta biết $$\lambda_1 + \lambda_2 = \lambda p + \lambda (1-p) = \lambda \Rightarrow \lambda = \lambda_1 + \lambda_2 = 11$$.

- $$P(type 1) = \frac{\lambda_1}{\lambda} = \frac{10}{11}$$.

- $$P(type 2) = 1 - P(type 1) = \frac{1}{11}$$.

$$
\begin{aligned}
P\{ type 1 | claim \ge $4000 \} & = \frac{P\{\ge $4000 | 1\}P(1)}{P\{\ge $4000 | 1\}P(1) + P\{\ge $4000 | 2\}P(2)}\\
& = \frac{e^{-4000 \cdot 1/1000}(10/11)}{e^{-4000 \cdot 1/1000}(10/11) + e^{-4000 \cdot 1/5000}(1/11)} \\
& \approx 0.2896
\end{aligned}
$$

{: .new}
Quá trình Poisson tính đến thời điểm này được gọi là quá trình Poisson thuần nhất (Homogeneous Poisson Process) do tham số $$\lambda$$ là hằng số.

{: .note-title}
> Quá trình Poisson không thuần nhất (Nonhomogeneous)
>
> Một quá trình đếm $$\{ N(t) \}, t \ge 0$$ là một quá trình Poisson không thuần nhất với hàm cường độ $$\lambda(t), t ge 0$$ nếu
> 1. Giá trị xuất phát tại $$N(0) = 0$$.
> 2. Tính độc lập (independence): $$N$$ có tính chất số gia độc lập. Chẳng hạn, số lượng biến cố xảy ra tại các khoảng thời gian không giao nhau (disjoint time) là độc lập.
> 3. Tính thuần nhất (homogeneity): Phân phối xác suất của số lượng biến cố trong một khoảng thời gian chỉ phụ thuộc vào độ dài của khoảng thời gian đó, $$P(N(t + h) - N(t) = 1) = \lambda(t)) h + o(h)$$. Nói cách khác, nếu cho một khoảng thời gian (time duration) xác định, thì xác suất xảy ra $$k$$ sự kiện là như nhau dù khoảng này nằm ở thời điểm nào.
> 4. Tính không đồng thời (non-concurrence): Xác suất để ít nhất hai biến cố xảy ra đồng thời tại một điểm  có độ dài $$h$$ là rất nhỏ, $$P(N(t + h) - N(t) \ge 2) = o(h)$$.
>
> *trong đó, $$o(h)$$ là $$lim_{h \to 0}\frac{f(h)}{h} = 0$$*.

{: .note-title}
> Bổ đề
>
> Nếu $$\{ N(t), t \ge 0 \}$$ là một quá trình Poisson không thuần nhất với hàm cường độ $$\lambda(t)$$ thì:
>
> $$P\{ N(t) = 0 \} = e^{-m(t)}$$
>
> với hàm $$m(t)$$ được gọi là hàm giá trị trung bình, được định nghĩa
>
> $$m(t) = \int_0^t \lambda(y)dy$$


# References

MIT OpenCourseWare. (n.d.). L22.2 Definition of the Poisson Process \[Video\]. YouTube. https://www.youtube.com/watch?v=D_EGYzqmapc

Nguyen Huu, Thai (n.d.). Lecture: Poisson Process. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

