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

Trong lý thuyết xác suất, **giá trị kỳ vọng** cơ bản là kết quả trung bình chúng ta sẽ nhận được nếu bạn có thể lặp lại một thí nghiệm đi đi lại lại. Nó được tính toán bằng cách nhân mỗi kết quả có thể xảy ra với xác suất của nó và sau đó cộng tất cả những sản phẩm đó lại với nhau.

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
3. Nếu biến $$X \le Y$$ luôn luôn (ordering rule): $$E[X] \le E[Y]$$.
4. Kỳ vọng của tổng bằng tổng các kỳ vọng (additive rule): $$E[X + Y] = E[X] + E[Y]$$.

**Trường hợp đặt biệt của kỳ vọng:**

Ví dụ, biến ngẫu nhiên liên tục $$X$$ có phân phối chuẩn trên đoạn đóng [0, 1]. Cho $$T = X^2$$. Tính kỳ vọng $$E[T]$$. Để tính được kỳ vọng này, sử dụng công thức dưới đây:

{: .highlight }
$$
E[g(X)] = \begin{cases}
\int_x g(x)f_X(x)dx \text{ , for continuous rv} \\
\sum_x g(x)f_X(x) \text{ , for discrete rv}
\end{cases}
$$

Đặt $$g(x) = x^2$$. Vì X tuân theo phân phối chuẩn nên hàm PDF $$f_X(x) = \frac{1}{1 - 0} = 1$$. Kỳ vọng của $$E(T)$$:


$$E(T) = E(X^2) = \int_{0}^{1} x^2 \cdot 1 dx = \left[\frac{x^3}{3}\right]_{0}^{1} = \frac{1}{3}$$

Trong đó, $$E[X^2]$$ còn được gọi là **moment bậc 2** của X.


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

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Penn State Department of Statistics. (n.d.). Lesson 9: Moment generating functions. https://online.stat.psu.edu/stat414/book/export/html/676

Ross, S. M. (2019). Introduction to probability models. Academic Press.