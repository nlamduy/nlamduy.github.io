---
layout: default
math: mathjax
title: Expected Value and Variance
parent: Random Variables
grand_parent: Stochastic Process
nav_order: 3
---

# Expected Value and Variance
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

**Giá trị kỳ vọng và phương sai của một số phân phối xác suất rời rạc:**

| Phân phối                       | Kỳ vọng, E[X]      | Phương sai, Var(X)                                     |
|---------------------------------|--------------------|--------------------------------------------------------|
| Nhị thức (binomial)             | $$np$$             | $$np(1-p)$$                                            |
| Poisson                         | $$\lambda$$        | $$\lambda$$                                            |
| Hình học (geometric)            | $$\frac{1}{p}$$    | $$\frac{1-p}{p^2}$$                                    |
| Nhị thức âm (negative binomial) | $$\frac{r}{p}$$    | $$r\frac{1-p}{p^2}$$                                   |
| Siêu bội (hypergemetric)        | $$n(\frac{r}{N})$$ | $$n(\frac{r}{N})(1-\frac{r}{N})(\frac{N - n}{N - 1})$$ |

**Giá trị kỳ vọng và phương sai của một số phân phối xác suất liên tục:**

| Phân phối        | Kỳ vọng, E[X]           | Phương sai, Var(X)         |
|------------------|-------------------------|----------------------------|
| Đều (uniform)    | $$ \frac{a + b}{2} $$   | $$ \frac{(b - a)^2}{12} $$ |
| Mũ (exponential) | $$ \frac{1}{\lambda} $$ | $$ \frac{1}{\lambda^2} $$  |
| Gamma            | $$ \frac{n}{\lambda} $$ | $$ \frac{n}{\lambda^2} $$  |
| Chuẩn (normal)   | $$ \mu $$               | $$ \sigma^2 $$             |

# Expected value

Trong lý thuyết xác suất, **giá trị kỳ vọng** cơ bản là kết quả trung bình chúng ta sẽ nhận được nếu có thể lặp lại một thí nghiệm nhiều lần. Nó được tính toán bằng cách nhân mỗi kết quả có thể xảy ra với xác suất của nó và sau đó cộng tất cả những tích đó lại với nhau.

## Discrete random variable

{: .highlight }
> Giá trị kỳ vọng cho biến ngẫu nhiên rời rạc:
>
> $$
> E(X) = \sum_x xf_X(x)
> $$

Ví dụ: dữ liệu về số xe bán được trong 1 ngày và xác suất tương ứng.

| x | f(x) | xf(x) |
|---|------|-------|
| 0 | 0.18 | 0.00  |
| 1 | 0.39 | 0.39  |
| 2 | 0.24 | 0.48  |
| 3 | 0.14 | 0.42  |
| 4 | 0.04 | 0.16  |
| 5 | 0.01 | 0.05  |
|   |      |E(X) = 1.5|

Số xe kỳ vọng bán được trong 1 ngày: $$E(X) = 1.5$$ xe. Từ đây cũng có thể suy ra số xe kỳ vọng bán được trong một tháng là 1.5*30 = 45 xe.

## Continuous random variable

{: .highlight }
> Giá trị kỳ vọng cho biến ngẫu nhiên liên tục:
>
> $$
> E(X) = \int_{-\infty}^{\infty} xf_X(x)dx
> $$

Ví dụ: Cho ngẫu nhiên liên tục Z có hàm mật độ xác suất (PDF) như sau:

$$ f(z) = \begin{cases} 
      2z & \text{if } 0 \leq z \leq 1 \\
      0 & \text{otherwise}
   \end{cases}
$$

Giá trị kỳ vọng của Z được tính bằng:

$$
\begin{aligned}
& E[Z] = \int_{-\infty}^{\infty} z f(z) \\
& E[Z] = \int_{0}^{1} z \cdot 2z dz = 2 \cdot \left[\frac{z^3}{3}\right]_0^1 = \frac{2}{3}
\end{aligned}
$$

{: .note-title }
> Một số tính chất cơ bản của kỳ vọng
> 1. Kỳ vọng của một hằng số bằng chính hằng số đó (constancy rule): $$E[c] = c$$.
> 2. Nếu tồn tại hằng số c trong dấu kỳ vọng (scaling rule): $$E[cX] = cE[X]$$.
> 3. Nếu biến $$X \le Y$$ (ordering rule): $$E[X] \le E[Y]$$.
> 4. Kỳ vọng của tổng bằng tổng các kỳ vọng (additive rule): $$E[X + Y] = E[X] + E[Y]$$.


**Trường hợp đặt biệt của kỳ vọng:**

Ví dụ, biến ngẫu nhiên liên tục $$X$$ có phân phối chuẩn trên đoạn [0, 1]. Cho $$T = X^2$$. Tính kỳ vọng $$E[T]$$. Để tính được kỳ vọng này, sử dụng công thức dưới đây:

{: .highlight }
$$
E[g(X)] = \begin{cases}
\int_x g(x)f_X(x)dx \text{ , for continuous rv} \\
\sum_x g(x)f_X(x) \text{ , for discrete rv}
\end{cases}
$$

Đặt $$g(x) = x^2$$. Vì X tuân theo phân phối chuẩn nên hàm PDF $$f_X(x) = \frac{1}{1 - 0} = 1$$. Kỳ vọng của $$E(T)$$:


$$E(T) = E(X^2) = \int_{0}^{1} x^2 \cdot 1 dx = \left[\frac{x^3}{3}\right]_{0}^{1} = \frac{1}{3}$$

Trong đó, $$E[X^2]$$ còn được gọi là **moment bậc 2** của X. Lưu ý, $$E[X^2] \ne (E[X])^2$$.


# Moment generating function

Các kỳ vọng $$E[X], E[X^2], E[X^3], ..., E[X^r]$$ được gọi là moments. Đôi khi việc tìm trung bình $$\mu = E[X]$$ hay phương sai $$\sigma^2 = Var[X] = E[X^2] - (E[X])^2$$ (functions of moments) là khó khăn. Hàm sinh moment có thể giúp việc này đơn giản hơn.


{: .highlight }
> Hàm sinh moment (MGF) là một phép biến đổi Laplace (Laplace transformation) trên hàm mật độ xác suất (PDF), được định nghĩa bằng:
> 
> $$
> \phi(t) = E[e^{tX}] = \begin{cases}
> \sum_x e^{tx} p(x) \text{ , if X is discrete}\\
> \int_{-\infty}^{\infty} e^{tx} f(x)dx \text{ , if X is continuous}
> \end{cases}
> $$

Ví dụ 1:

$$
\begin{aligned}
& \phi'(t) = \frac{d}{dt}E[e^{tX}]\\
& = E[\frac{d}{dt}(e^{tX})]\\
& = E[Xe^{tX}]
\end{aligned}
$$

Nếu $$t = 0$$,

$$
\phi'(t) = E[X]
$$

Tương tự, lấy đạo hàm bậc 2,

$$
\phi''(t) = E[X^2 e^{tX}] = E[X^2] \text{ , if t = 0}
$$



{: .highlight }
> Tổng quát, **để tìm $$E[X^n]$$ thì chỉ cần lấy n-bậc đạo hàm của hàm MGF với t = 0**:
> 
> $$
> \phi^n(0) = E[X^n] \text{ , } n \ge 1
> $$

**Ứng dụng của hàm MGF:**
- Kỳ vọng và phương sai của biến ngẫu nhiên.
- Hàm PMF của biến ngẫu nhiên.

{: .note }
> - Từ một hàm PDF, chỉ tính được duy nhất một hàm MGF. Hay nói cách khác, mỗi phân phối chỉ có một dạng hàm MGF. Như vậy, hàm MGF (nếu tồn tại) là đặc trưng của phân phối đó.
> - Nếu $$\phi_X(t) = \phi_Y(t)$$ thì X và Y có cùng phân phối.




{: .highlight }
> **Một số tính chất của hàm MGF:**
>
> 1. $$\phi^n(0) = E[X^n], n \ge 1$$
> 2. $$\phi_{X + Y}(t) = \phi_X(t)\phi_Y(t) \text{ , if X and Y are independent}$$


**Hàm MGF của một số phân phối rời rạc:**

| Phân phối                       | Hàm sinh moment (MGF), $$\phi(t)$$ | Moment bậc 1, $$\phi^{'}(t)$$           | Moment bậc 2, $$\phi^{''}(t)$$                                               |
|---------------------------------|------------------------------------|-----------------------------------------|------------------------------------------------------------------------------|
| Nhị thức (binomial)             | $$ (pe^t + (1 - p))^n $$           | $$ n(pe^t + 1 - p)^{n - 1}pe^t $$       | $$ n(n - 1)(pe^t + 1 - p)^{n - 2}(pe^t)^2 + n(pe^t + 1 - p)^{n - 1}pe^t $$   |
| Poisson                         | $$ e^{\lambda(e^t - 1)} $$         | $$ \lambda e^t e^{\lambda (e^t - 1)} $$ | $$ (\lambda e^t)^2 e^{\lambda(e^t - 1)} + \lambda e^t e^{\lambda(e^t -1)} $$ |
| Hình học (geometric)            | $$ \frac{pe^t}{1 - (1 - p)e^t} $$  |                                         |                                                                              |
| Nhị thức âm (negative binomial) |                                    |                                         |                                                                              |
| Siêu bội (hypergemetric)        |                                    |                                         |                                                                              |


**Hàm MGF của một số phân phối liên tục:**

| Phân phối        | Hàm sinh moment (MGF), $$\phi(t)$$       | Moment bậc 1, $$\phi^{'}(t)$$                               | Moment bậc 2, $$\phi^{''}(t)$$$$                                                                            |
|------------------|------------------------------------------|-----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| Đều (uniform)    | $$ \frac{e^{tb} - e^{ta}}{t(b-a)} $$     |                                                           |                                                                                                           |
| Mũ (exponential) | $$ \frac{\lambda}{\lambda - t} $$        | $$ \frac{\lambda}{(\lambda - t)^2} $$                     | $$ \frac{2\lambda}{(\lambda - t)^3} $$                                                                    |
| Gamma            | $$ (\frac{\lambda}{\lambda - t})^n $$    |                                                           |                                                                                                           |
| Chuẩn (normal)   | $$ e^{\mu t + \frac{\sigma^2 t^2}{2}} $$ | $$ (\mu + t\sigma^2)e^{\frac{\sigma^2 t^2}{2} + \mu t} $$ | $$ (\mu + t\sigma^2)^2 e^{\frac{\sigma^2 t^2}{2} + \mu t} + \sigma^2 e^{\frac{\sigma^2 t^2}{2} + \mu t} $$ |

{: .new }
Có thể thấy, **nếu $$t = 0$$ thì hàm MGF bậc 1 sẽ chính bằng kỳ vọng của phân phối.** MGF bậc 2 khi $$t = 0$$ chính bằng $$E[X^2]$$ và được sử dụng để tính phương sai với $$\text{Var}(X) = E[X^2] - (E[X])^2$$ 

# Join probability distribution

Phân phối xác suất đồng thời của hai biến ngẫu nhiên X và Y đã được giới thiệu qua trong phần [xác suất có điều kiện](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities).

{: .highlight }
> Xác suất của X và Y đồng thời cùng xảy ra được định nghĩa:
> 
> $$
> F(a, b) = P\{X \le a, Y \le b\} \text{ , } -\infty < a, b < \infty
> $$



{: .note-title }
> Một số tính chất của xác suất đồng thời
> 
> 1. Đạo hàm cấp 2 hàm CDF của phân phối đồng thời sẽ được hàm PDF: $$\frac{d^2}{dxdy}F_{X,Y}(x, y) = f_{X,Y}(x, y)$$.
> 2. Hàm CDF của phân phối biên: $$F_X(a) = F(a, \infty)$$, và $$F_Y(b) = F(\infty, b)$$.
> 3. Phân phối đồng thời rời rạc: $$p_X(x) = \sum_{y:p(x,y)>0} p(x,y)$$, và $$p_Y(y) = \sum_{x:p(x,y)>0} p(x,y)$$.
> 4. Phân phối đồng thời liên tục: $$f_X(x) = \int_{-\infty}^{\infty} f(x,y)dy$$, $$f_Y(y) = \int_{-\infty}^{\infty} f(x,y)dx$$, và $$\frac{d^2}{dadb}F(a,b)=f(a,b)$$.
> 5. Cho $$g$$ là hàm của biến X, Y:
> $$
> E[g(X,Y)] = \begin{cases}
> \sum_y \sum_x g(x,y) p(x,y) \text{ , in the discrete case}\\
> \int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x,y)f(x,y)dxdy \text{ , in the continuous case}
> \end{cases}
> $$

Ví dụ: 

Cho hàm xác suất đồng thời:

$$
f(x,y) = \begin{cases}
6xy(2 - x - y), 0 < x < 1, 0 < y < 1 \\
0 \text{ , otherwise}
\end{cases}
$$

Tính xác suất biên $$f_X(x)$$.

Ta có:

$$
\begin{aligned}
& \int_{-\infty}^{\infty} f_{X,Y}(x,y)dy = \int_0^1 f_{X,Y}(x,y)dy\\
& = \int_0^1 6xy(2 - x - y)dy = \left[ 12x \frac{y^2}{2} - 6x^2\frac{y^2}{2} - 6x\frac{y^3}{3} \right]^1_0\\
& = 4x - 3x^2\\
\end{aligned}
$$

Như vậy:

$$
f_X(x) = \begin{cases}
4x - 3x^2 \text{ , if 0 < x < 1}\\
0 \text{ , otherwise}
\end{cases}
$$

## Discrete random variable



{: .highlight }
> Nếu **X và Y là hai biến ngẫu nhiên rời rạc**:
> 
> $$
> p(x, y) = P\{X = x, Y = y\}
> $$

Một cách hình học, có thể diễn tả xác suất đồng thời là diện tích (màu vàng) tạo bởi đường thẳng a, b cắt tại trục x, y tương ứng như hình bên dưới:

![joint_eg1](/assets/img/stochastic-process/joint_eg1.png)

## Continuous random variable



{: .highlight }
> Nếu **X và Y là hai biến ngẫu nhiên liên tục**:
> 
> $$
> P\{X \in A, Y \in B\} = \int_B \int_A f(x, y) dxdy \text{ , where } A, B \subset \mathbb{R}
> $$

Sử dụng định lý [Fubini](https://en.wikipedia.org/wiki/Guido_Fubini) **(Fubini's Theorem) để xử lý tích phân bội (double integral)** ở trên, ta được:

{: .highlight }
> Cách 1:
> 
> $$
> \int_a^b \left( \int_{h(x)}^{g(x)} f(x,y)dy \right) dx
> $$

hoặc,

{: .highlight }
> Cách 2:
> 
> $$
> \int_{h(x)}^{g(x)}\left( \int_a^b f(x,y)dx \right)dy
> $$

*Việc lấy tích phân theo $$dy$$ hay $$dx$$ trước là tuỳ ý vì kết quả là như nhau.* 

![joint_eg2](/assets/img/stochastic-process/joint_eg2.png)

Ví dụ:

Tính tích phân bội của hàm số sau:

$$
\int \int 6xy(2 - x - y)dxdy \text{ , 0 < x < 0.5, 0 < y < 1}
$$

Áp dụng định lý Fubini:

$$
\begin{aligned}
& \int_0^{0.5} \left( \int_0^1 6xy(2 - x - y) dy \right)dx\\
& = \int_0^{0.5} \left( \left[ 12x \frac{y^2}{2} - 6x^2\frac{y^2}{2} - 6x\frac{y^3}{3} \right] ^1_0 \right)dx \\

& = \int_0^{0.5} (4x - 3x^2)dx\\
& = \left[ \frac{4x^2}{2} - \frac{3x^3}{3} \right]^{0.5}_0\\
& = \frac{3}{8}
\end{aligned}
$$

Sử dụng phần mềm GeoGebra để trực quan hoá. Xác suất đồng thời chính là thể tích của phần màu xám được tạo ra bởi giới hạn của $$x = [0; 0.5], y = [0; 1]$$ và hình dáng của hàm số $$f(x,y) = 6xy(2 - x - y)$$.

![joint_eg3](/assets/img/stochastic-process/joint_eg3.png)

# Independent random variables



{: .highlight }
> Hai biến ngẫu nhiên X, Y là độc lập cho mọi giá trị a, b nếu:
> 
> $$
> F(a, b) = P\{X \le a, Y \le b\} = P\{X \le a\}P\{Y \le b\} = F_X(a)F_Y(b)
> $$

- Đối với phân phối đồng thời cho biến rời rạc, hai biến độc lập nếu:
$$
p(x,y) = p_X(x)p_Y(y)
$$

- Đối với phân phối đồng thời cho biến liên tục, hai biến độc lập nếu:
$$
f(x,y) = f_X(x)f_Y(y)
$$

- Nếu X, Y độc lập thì hai hàm số h, g bất kỳ:
$$
E[g(X)h(Y)] = E[g(X)]E[h(Y)]
$$

Điều này vẫn đúng cho trường hợp: $$E[X^2Y] = E[X^2]E[Y]$$.

# Variance and Covariance

## Variance



{: .highlight }
> **Phương sai (variance) của một biến ngẫu nhiên cho biết sự phân tán của dữ liệu xung quanh giá trị kỳ vọng**. Được định nghĩa:
> 
> $$
> \text{Var}(X) = E[X^2] - (E[X])^2
> $$
>
> *Trong đó, $$E[X^2]$$ là moment bậc 2 của kỳ vọng $$E[X]$$.*


## Covariance

{: .highlight }
> **Hiệp phương sai (covariance) của hai biến ngẫu nhiên X, Y** cho biến sự phân tán **liên hợp** của hai biến này, được định nghĩa:
> 
> $$
> \text{cov}(X, Y) = E[(X - E(X))(Y - E(Y))] = E(XY) - E(X)(Y)
> $$

Từ biểu thức trên có thể thấy, **để tính được phương sai và hiệp phương sai, cần tính được kỳ vọng**.


{: note-title }
> Một số tính chất của hiệp phương sai
> 
> 1. Nếu X và Y độc lập: Cov(X, Y) = 0
> 2. Cov(X,Y) = Cov(Y,X)
> 3. Cov(X,X) = Var(X)
> 4. Cov(cX, Y) = cCov(X, Y)
> 5. Cov(X, Y + Z) = Cov(X, Y) + Cov(X, Z)
> 6. $$\text{Var}(\sum_{i = 1}^n X_i) = \sum_{i = 1}^n \text{Var}(X_i) + 2\sum^n_{i=1} \sum_{j<i}\text{Cov}(X_i, X_j)$$

**Tính chất 4, 5, 6 là quan trọng**. Trong đó, tính chất 6 phát biểu rằng, nếu **$${X_1, X_2, ..., X_n}$$ là độc lập** thì $$2\sum^n_{i=1} \sum_{j<i}\text{Cov}(X_i, X_j) = 0$$, hay $$\text{Var}(\sum_{i = 1}^n X_i) = \sum_{i = 1}^n \text{Var}(X_i)$$.

Ví dụ:

Hàm phân phối đồng thời của X, Y được cho bởi: $$f(x,y) = \frac{1}{y}e^{-(y + x/y)}$$, $$0 < x, y < \infty$$. Tìm Cov(X,Y).

$$\text{Cov}(X,Y) = E[XY] - E[X]E[Y]$$

- Tính E[XY]:
$$
E[XY] = \int_0^{\infty} \left( \int_0^{\infty} \frac{1}{y}e^{-(y + x/y)} dx\right)dy
$$

- Tính E[X]:
$$
E[X] = f_X(x) = \int_0^{} f_{X, Y}(x, y)dy
$$

- Tính E[Y]:
$$
E[Y] = f_Y(y) = \int f_{X, Y}(x, y)dx
$$

# Markov's inequality

Bất đẳng thức [Markov](https://vi.wikipedia.org/wiki/Andrey_Andreyevich_Markov) giúp chúng ta **đánh giá nhanh (mặc dù không phải tốt nhất) xác suất đuôi của phân phối**.

{: .highlight }
>  Nếu X là biến ngẫu nhiên chỉ nhận giá trị không âm, thì với bất kỳ giá trị $$a > 0$$, bất đẳng thức Markov là:
> 
> $$
> P\{ X \ge a \} \le \frac{E[X]}{a}
> $$

Thông thường, chúng ta có thể tính toán xác suất dựa trên hàm PMF/PDF đã xác định. Tuy nhiên, không phải lúc nào chúng ta cũng biết được các hàm này mà chỉ có trong tay giá trị trung bình. 

Ví dụ: sử dụng lại vấn đề của Công ty lốp xe Grear ở phần [phân phối chuẩn chuẩn hoá](https://nlamduy.github.io/docs/stochastic-process/random-variables/continuous-random-variable.html#standard-normal-distribution). Ta có trung bình $$E[X] = 36500$$km, và xác suất thực tế $$P\{X > 40000\} \approx 0.2420$$. 

Giả sử, ta không biết biến ngẫu nhiên X tuân theo phân phối chuẩn chuẩn hoá mà chỉ có thông tin về trung bình $$E[X]$$. Sử dụng bất đẳng thức Markov để ước lượng, ta được: 

$$
P\{X \ge 40000\} \le \frac{36500}{40000} = 0.9125
$$. 

Xác suất lốp xe chịu được tối thiểu 40,000km là 91.25%. Có thể thấy xác suất này sai số rất lớn so với thực tế là 24.20%. Liệu chúng ta có thể tìm được ước lượng nào tốt hơn bất đẳng thức Markov? Đây chính là động lực cho bất đẳng thức Chebyshev.

# Chebyshev's inequality

Nếu biết phương sai, bất đẳng thức [Chebyshev](https://vi.wikipedia.org/wiki/Pafnuty_Lvovich_Chebyshev) sẽ cho ước lượng tốt hơn bất đẳng thức Markov. 

{: .highlight }
> Nếu X là biến ngẫu nhiên độc lập có trung bình $$\mu$$ và phương sai $$\sigma^2$$, với bất kỳ giá trị $$k > 0$$, bất đẳng thức Chebyshev cho ta:
> Cách 1:
> 
> $$
> P\{|X - \mu| \ge k\} \le \frac{\sigma^2}{k^2}
> $$

hoặc

{: .highlight }
> Cách 2:
>
> $$
> P\{|X - \mu| \ge k\sigma\} \le \frac{1}{k^2}
> $$

*Bất đẳng thức Chebyshev cho phép X nhận giá trị âm.*

{:. warning }
Một điểm quan trọng là $$k > \sigma^2$$ hoặc $$k \ge 1$$. Nếu điều kiện này không thoả, xác suất tính ra sẽ lơn hơn 1.

Ví dụ:

Sử dụng lại ví dụ của Công ty lốp xe Grear ở phần [phân phối chuẩn chuẩn hoá](https://nlamduy.github.io/docs/stochastic-process/random-variables/continuous-random-variable.html#standard-normal-distribution), nhưng lần này muốn ước lượng xác suất khi $$X \ge 42000$$km. Ta biết trung bình $$\mu = 36500$$ và phương sai $$\sigma^2 = 5000^2$$ và X tuân theo phân phối chuẩn. Có thể dễ dàng tính được xác suất $$P\{ X \ge 42000 \} \approx 0.1357$$.

Giả sử ta không có thông tin về phân phối của X, mà chỉ có trung bình và phương sai, thì ước lượng từ các bất đẳng thức như thế nào?

- Sử dụng bất đẳng thức Markov (chỉ có thông tin về trung bình):
$$
P\{X \ge 42000\} \le \frac{36500}{42000} \approx 0.8690
$$

- Sử dụng bất đẳng thức Chebyshev (có thông tin về trung bình và phương sai):
$$
P\{|42000 - 36500| \ge 5500\} \le \frac{5000^2}{5500^2} \approx 0.8264
$$

{: .new }
Như vậy, bất đẳng thức Chebyshev cho kết quả gần với thực tế (P = 0.1357) hơn là bất đẳng thức Markov.

# Strong law of large number



{: .hightlight }
> Định lý luật số lớn phát biểu rằng, cho $$X_1, X_2, ...$$ là một dãy các biến ngẫu nhiên độc lập và có phân phối giống nhau thì:
> 
> $$
> \frac{X_1 + X_2 + ... + X_n}{n} \rightarrow \mu \text{ as } n \to \infty
> $$

Nói cách khác, nếu chúng ta lấy mẫu 1, mẫu 2 , ..., mẫu n với phân phối giữa các mẫu là giống nhau, và lấy trung bình của mẫu. Thì trung bình mẫu $$E[X_i]$$ sẽ tiến gần tới trung bình thực tế $$\mu$$.

# Central limit theorem



{: .highlight }
> Định lý giới hạn trung tâm phát biểu rằng, cho $$X_1, X_2, ..., X_n$$ là một dãy các biến ngẫu nhiên độc lập có cùng phân phối với trung bình $$\mu$$ và phương sai $$\sigma^2$$. Thì phân phối của $$\frac{X_1 + X_2 + ... + X_n - n\mu}{\sigma\sqrt{n}}$$ tiến về phân phối chuẩn chuẩn hoá khi $$n \to \infty$$.
> 
> $$
> P\{\frac{X_1 + X_2 + ... + X_n - n\mu}{\sigma\sqrt{n}} \le a\} \to \frac{1}{\sqrt{2\pi}}\int_{-\infty}^a e^{-x^2/2} dx 
> $$

{: .important }
Định lý giới hạn trung tâm được chứng minh **đúng cho bất kỳ phân phối** nào của $$X_i$$.

Có thể sử dụng một số công cụ giả lập CLT trên internet để quan sát định lý trên.

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Dartmouth Mathematics. (n.d.). Math 20 – Inequalities of Markov and Chebyshev. math.dartmouth.edu.

Department of Mathematics, University of Texas at Austin. (n.d.). Fubini’s theorem. M408M Learning Module Pages. https://web.ma.utexas.edu/users/m408m/Display15-2-3.shtml

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Penn State Department of Statistics. (n.d.). Lesson 9: Moment generating functions. https://online.stat.psu.edu/stat414/book/export/html/676

Ross, S. M. (2019). Introduction to probability models. Academic Press.
