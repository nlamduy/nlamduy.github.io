---
layout: default
math: mathjax
title: Continuous Random Variable
parent: Probability Theory
grand_parent: Stochastic Process
nav_order: 2
---

# Continuous Random Variable
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

Biến ngẫu nhiên liên tục **nhận bất kỳ giá trị nào** trong một khoảng cho trước.

Ví dụ:

| **Example** | **Description** | **Possible Values** |
|-------------|-----------------|---------------------|
| Height of Students in a Class | The height of students in a class is a continuous random variable. | Real numbers (e.g., heights in centimeters) |
| Amount of Iced Tea in a Glass | The amount of iced tea in a glass is another continuous random variable.  | Real numbers (e.g., volume in milliliters) |
| Change in Temperature Throughout a Day | The change in temperature over the course of a day is a continuous random variable.  | Real numbers (e.g., degrees Celsius or Fahrenheit) |

# Probability density function

Hàm mật độ xác suất (PDF) của một biến ngẫu nhiên liên tục X được tính bằng:

{:. highlight }

$$
P\{X \in B\} = \int_B f_X(x)dx
$$

Trong đó: $$B \subset \mathbb{R}$$


Ví dụ:

Tính xác suất $$P\{X > 3\}$$ với $$B = (3, +\infty)$$: $$P\{X > 3\} = \int_3^{+\infty} f_X(x)dx$$.

**Một số tính chất cơ bản:**

- Xác suất của biến ngẫu nhiên liên tục X nằm giữa đoạn $$(a,b)$$ là tích phân của hàm $$f_X$$ trên đoạn đó: $$P\{a \le X \le b\} = \int_a^b f_X(x)dx$$, cho $$a \le b$$

- Xác suất của biến ngẫu nhiên liên tục X tại một điểm cụ thể bằng 0: $$P\{X = a\} = \int_a^a f_X(x)dx = 0$$

- Xác suất từ âm đến dương vô cực là 1: $$\int_{-\infty}^{+\infty} f_X(x)dx = 1$$

- CDF của X là nguyên hàm trên đoạn $$(-\infty, x)$$: $$F_X(x) = \int_{-\infty}^x f_X(x)dx$$

- PDF của X là đạo hàm CDF: $$\frac{dF(x)}{dx} = f(x)$$

Ví dụ:

Cho hàm mật độ xác suất của X:

$$
f_X(x) = \begin{cases} 
\frac{10}{x^2}  & \text{ , for } x > 10 \\
0 & \text{ , otherwise}
\end{cases}
$$

Tìm xác suất $$P\{X > 20\}$$.

$$
P\{X > 20\} = \int_{20}^{\infty} f_X(x) dx = \int_{20}^{\infty} \frac{10}{x^2} dx
$$

$$
\int_{20}^{\infty} \frac{10}{x^2} dx = \left[ -\frac{10}{x} \right]_{20}^{\infty} = 0 - (-\frac{10}{20}) = \frac{1}{2}
$$

Trực quan hoá với Python:

![pdf_example1](https://github.com/nlamduy/nlamduy.github.io/blob/3336c810381c58bf328747cc2d2190ef320c4a23/_assets/img/pdf_eg1.png)




## References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.