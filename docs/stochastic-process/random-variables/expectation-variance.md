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

# Expected value

Trong lý thuyết xác suất, **giá trị kỳ vọng** cơ bản là kết quả trung bình chúng ta sẽ nhận được nếu có thể lặp lại một thí nghiệm nhiều lần. Nó được tính toán bằng cách nhân mỗi kết quả có thể xảy ra với xác suất của nó và sau đó cộng tất cả những tích đó lại với nhau.

## Discrete random variable

**Giá trị kỳ vọng cho biến ngẫu nhiên rời rạc:**

{: .highlight }

$$
E(X) = \sum_x xf_X(x)
$$

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

**Giá trị kỳ vọng cho biến ngẫu nhiên liên tục:**

{: .highlight }

$$
E(X) = \int_{-\infty}^{\infty} xf_X(x)dx
$$

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


**Một số tính chất cơ bản của kỳ vọng:**

{: .highlight }
1. Kỳ vọng của một hằng số bằng chính hằng số đó (constancy rule): $$E[c] = c$$.
2. Nếu tồn tại hằng số c trong dấu kỳ vọng (scaling rule): $$E[cX] = cE[X]$$.
3. Nếu biến $$X \le Y$$ (ordering rule): $$E[X] \le E[Y]$$.
4. Kỳ vọng của tổng bằng tổng các kỳ vọng (additive rule): $$E[X + Y] = E[X] + E[Y]$$.

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

Hàm sinh moment (MGF) là một phép biến đổi Laplace (Laplace transformation) trên hàm mật độ xác suất (PDF), được định nghĩa bằng:

{: .highlight }
$$
\phi(t) = E[e^{tX}] = \begin{cases}
\sum_x e^{tx} p(x) \text{ , if X is discrete}\\
\int_{-\infty}^{\infty} e^{tx} f(x)dx \text{ , if X is continuous}
\end{cases}
$$

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

Tổng quát, **để tìm $$E[X^n]$$ thì chỉ cần lấy n-bậc đạo hàm của hàm MGF với t = 0**:

{: .highlight }
$$
\phi^n(0) = E[X^n] \text{ , } n \ge 1
$$

Hàm MGF được sử dụng để tìm:
- Kỳ vọng và phương sai của biến ngẫu nhiên.
- Hàm PMF của biến ngẫu nhiên.


Khi tính hàm MGF, có hai lưu ý:
- Từ một hàm PDF, chỉ tính được duy nhất một hàm MGF. Hay nói cách khác, mỗi phân phối chỉ có một dạng hàm MGF. Như vậy, hàm MGF (nếu tồn tại) là đặc trưng của phân phối đó.
- Nếu $$\phi_X(t) = \phi_Y(t)$$ thì X và Y có cùng phân phối.


**Một số tính chất của hàm MGF:**

{: .highlight }

1. $$\phi^n(0) = E[X^n], n \ge 1$$
2. $$\phi_{X + Y}(t) = \phi_X(t)\phi_Y(t) \text{ , if X and Y are independent}$$

# Join probability distribution

Phân phối xác suất đồng thời của hai biến ngẫu nhiên X và Y đã được giới thiệu qua trong phần [xác suất có điều kiện](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities). Trong phần này, xác suất của X và Y đồng thời cùng xảy ra được định nghĩa:

{: .highlight }
$$
F(a, b) = P\{X \le a, Y \le b\} \text{ , } -\infty < a, b < \infty
$$

**Một số tính chất của xác suất đồng thời:**

{: .highlight }

1. Đạo hàm cấp 2 hàm CDF của phân phối đồng thời sẽ được hàm PDF: $$\frac{d^2}{dxdy}F_{X,Y}(x, y) = f_{X,Y}(x, y)$$.
2. Hàm CDF của phân phối biên: $$F_X(a) = F(a, \infty)$$, và $$F_Y(b) = F(\infty, b)$$.
3. Phân phối đồng thời rời rạc: $$p_X(x) = \sum_{y:p(x,y)>0} p(x,y)$$, và $$p_Y(y) = \sum_{x:p(x,y)>0} p(x,y)$$.
4. Phân phối đồng thời liên tục: $$f_X(x) = \int_{-\infty}^{\infty} f(x,y)dy$$, $$f_Y(y) = \int_{-\infty}^{\infty} f(x,y)dx$$, và $$\frac{d^2}{dadb}F(a,b)=f(a,b)$$.
5. Cho $$g$$ là hàm của biến X, Y:
$$
E[g(X,Y)] = \begin{cases}
\sum_y \sum_x g(x,y) p(x,y) \text{ , in the discrete case}\\
\int_{-\infty}^{\infty} \int_{-\infty}^{\infty}g(x,y)f(x,y)dxdy \text{ , in the continuous case}
\end{cases}
$$

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

Nếu **X và Y là hai biến ngẫu nhiên rời rạc**:

{: .highlight }
$$
p(x, y) = P\{X = x, Y = y\}
$$

Một cách hình học, có thể diễn tả xác suất đồng thời là diện tích (màu vàng) tạo bởi đường thẳng a, b cắt tại trục x, y tương ứng như hình bên dưới:

![joint_eg1](/assets/img/stochastic-process/joint_eg1.png)

## Continuous random variable

Nếu **X và Y là hai biến ngẫu nhiên liên tục**:

{: .highlight }
$$
P\{X \in A, Y \in B\} = \int_B \int_A f(x, y) dxdy \text{ , where } A, B \subset \mathbb{R}
$$

Sử dụng định lý [Fubini](https://en.wikipedia.org/wiki/Guido_Fubini) **(Fubini's Theorem) để xử lý tích phân bội (double integral)** ở trên, ta được:

{: .highlight }
$$
\int_a^b \left( \int_{h(x)}^{g(x)} f(x,y)dy \right) dx
$$

hoặc,

{: .highlight }
$$
\int_{h(x)}^{g(x)}\left( \int_a^b f(x,y)dx \right)dy
$$

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

Hai biến ngẫu nhiên X, Y là độc lập cho mọi giá trị a, b nếu:

{: .highlight }
$$
F(a, b) = P\{X \le a, Y \le b\} = P\{X \le a\}P\{Y \le b\} = F_X(a)F_Y(b)
$$

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

**Phương sai (variance) của một biến ngẫu nhiên cho biết sự phân tán của dữ liệu xung quanh giá trị kỳ vọng**. Được định nghĩa:

{: .highlight }
$$
\text{Var}(X) = E[X^2] - (E[X])^2
$$

**Trong đó, $$E[X^2]$$ là moment bậc 2 của kỳ vọng $$E[X]$$.**

## Covariance

**Hiệp phương sai (covariance) của hai biến ngẫu nhiên X, Y** cho biến sự phân tán **liên hợp** của hai biến này, được định nghĩa:

{: .highlight }
$$
\text{cov}(X, Y) = E[(X - E(X))(Y - E(Y))] = E(XY) - E(X)(Y)
$$

Từ biểu thức trên có thể thấy, **để tính được phương sai và hiệp phương sai, cần tính được kỳ vọng**.

**Một số tính chất của hiệp phương sai:**

{: .highlight }
1. Nếu X và Y độc lập: Cov(X, Y) = 0
2. Cov(X,Y) = Cov(Y,X)
3. Cov(X,X) = Var(X)
4. Cov(cX, Y) = cCov(X, Y)
5. Cov(X, Y + Z) = Cov(X, Y) + Cov(X, Z)
6. $$\text{Var}(\sum_{i = 1}^n X_i) = \sum_{i = 1}^n \text{Var}(X_i) + 2\sum^n_{i=1} \sum_{j<i}\text{Cov}(X_i, X_j)$$

**Tính chất 4, 5, 6 là quan trọng**. Trong đó, tính chất 6 phát biểu rằng, nếu **$${X_1, X_2, ..., X_n}$$ là độc lập** thì $$2\sum^n_{i=1} \sum_{j<i}\text{Cov}(X_i, X_j) = 0$$, hay $$\text{Var}(\sum_{i = 1}^n X_i) = \sum_{i = 1}^n \text{Var}(X_i)$$.

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Department of Mathematics, University of Texas at Austin. (n.d.). Fubini’s theorem. M408M Learning Module Pages. https://web.ma.utexas.edu/users/m408m/Display15-2-3.shtml

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Penn State Department of Statistics. (n.d.). Lesson 9: Moment generating functions. https://online.stat.psu.edu/stat414/book/export/html/676

Ross, S. M. (2019). Introduction to probability models. Academic Press.