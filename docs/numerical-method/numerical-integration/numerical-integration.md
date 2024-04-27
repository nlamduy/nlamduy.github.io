---
layout: default
math: mathjax
title: Numerical Integration
nav_order: 1
# has_children: true
parent: Numerical Methods
---

# Numerical Integration
{: .no_toc }

Tích phân bằng phương pháp số học liên quan đến việc xấp xỉ giá trị của một tích phân khi chúng ta không thể tìm được nguyên hàm, hoặc việc tính chính xác là không cần thiết.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Newton-Cotes Integration Formulas

Công thức Newton-Cotes là phương pháp phổ biến nhất để xấp xỉ tích phân.

## Trapezoidal rule

Nguyên tắc hình thang là công thức đầu tiên của Newtew-Cotes dạng đóng (closed form).

Ví dụ: Tính xấp xỉ của tích phân $$\displaystyle\int_{0.2}^{0.8} x \sqrt{1 - x^2} dx$$.

Chúng ta có thể lấy nguyên hàm và tính tích phân trên đoạn $$[0.2, 0.8]$$ là $$a = \left[ -\frac{1}{3}(1 - x^2)^{\frac{3}{2}} + C \right]^{0.8}_{0.2} \approx 0.24153$$. 

Giả sử không tính được nguyên hàm của hàm số này, hoặc thậm chí không tìm được công thức của hàm số $$f(x)$$ mà chỉ giá trị của $$f(x)$$ cho bởi $$x$$ như sau:

| x   | f(x)    |
|-----|---------|
| 0   | 0       |
| 0.2 | 0.19596 |
| 0.4 | 0.36661 |
| 0.6 | 0.48    |
| 0.8 | 0.48    |
| 1   | 0       |


Để xấp xỉ được diện tích giữa 2 điểm $$[0.2, 0.4]$$, có thể nối 2 điểm này và tính diện bên dưới đường thẳng như hình bên dưới:

![newton_cotes_eg1](/assets/img/numerical-methods/newton_cotes_eg1.png)

Không khó nhận ra, hình dạng tạo bởi đường thẳng nối hai điểm và $$x=0.2, x=0.8$$ là một hình thang. Trong phần [nội suy tuyến tính](https://nlamduy.github.io/docs/numerical-method/interpolation/#newton-interpolating-polynomials), một đường thằng nối 2 điểm được thể hiện bằng công thức:

$$
f_1(x) = f(x_0) + \frac{f(x_1) - f(x_0)}{x_1 - x_0}(x - x_0)
$$

Như vậy, **diện tích bên dưới đường thẳng này chính là tích phân trên đoạn $$[x_1, x_0]$$**:

$$
I = \displaystyle \int_{x_0}^{x_1} \left[ f(x_0) + \frac{f(x_1) - f(x_0)}{x_1 - x_0}(x - x_0) \right]dx
$$

{: .highlight}
> Kết quả của tích phân trên:
>
> $$
> I = (x_1 - x_0)\frac{f(x_0) + f(x_1)}{2}
> $$
> 
> *được gọi là quy tắc hình thang*

Áp dụng công thức này cho ví dụ hiện tại, ta được xấp xỉ:

$$
b = (0.8 - 0.2)\frac{0.19596 + 0.48}{2} \approx 0.202788
$$

Chia nhỏ $$[0.2, 0.8]$$ ra thành 4 đoạn đều nhau, ta được:

$$
\begin{aligned}
c & = (0.4 - 0.2)\frac{f(0.2) + f(0.4)}{2} \\
& + (0.6 - 0.4)\frac{f(0.4) + f(0.6)}{2} \\
& + (0.8 - 0.6)\frac{f(0.6) + f(0.8)}{2} \\
& \approx 0.23692
\end{aligned}
$$

{: .new}
Nếu chia đoạn $$[x_0, x_i]$$ thành nhiều đoạn có độ dài như nhau thì xấp xỉ càng gần với nghiệm thực tế $$a = 0.24153$$.

# References

Chapra, S. C., & Canale, R. P. (2016). Numerical methods for engineers. McGraw Hill.

Dao Nguyen, Anh (n.d.). Lecture: Numerical Integration. Numerical Methods. University of Economics HCMC.

GeoGebra (2024). Dynamic Mathematics Software. https://www.geogebra.org.