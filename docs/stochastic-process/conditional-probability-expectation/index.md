---
layout: default
title: Conditional Probability and Expectation
parent: Stochastic Process
math: mathjax
# has_children: true
nav_order: 3
---

# Conditional Probability and Expectation
{: .no_toc }

**Xác suất có điều kiện** là khả năng xảy ra của một sự kiện, giả sử rằng một sự kiện khác đã xảy ra. Đây là cách để tính toán xác suất mà có tính đến thông tin hiện có. **Kỳ vọng có điều kiện** là giá trị kỳ vọng của một biến ngẫu nhiên khi một điều kiện nhất định được thỏa mãn. Nó giống như lấy trung bình của một tập hợp các số, nhưng chỉ những số nào đáp ứng một tiêu chí cụ thể.

Xác suất có điều kiện đã được giới thiệu ở [đây](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities). Trong phần này sẽ được trình bày chi tiết hơn.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Discrete case

Cho X, Y là các biến ngẫu nhiên rời rạc với hàm khối xác suất đồng thời $$p(x, y)$$, **hàm khối xác suất có điều kiện** (conditional probability mass function) của X với điều kiện Y đã xảy ra ($$Y = y$$) được định nghĩa:

{: .highlight }
$$
p_{X|Y}(x|y) = P\{X = x | Y = y\} = \frac{P\{X = x, Y = y\}}{P\{Y = y\}} = \frac{p(x, y)}{p_Y(y)}
$$

với xác suất biên $$P\{Y = y\} > 0$$ cho mọi giá trị của $$y$$.

*Trong đó, $$P\{X = x, Y = y\}$$ là xác suất đồng thời và $$P\{Y = y\}$$ là xác suất biên.*

**Hàm xác suất tích luỹ có điều kiện** (conditional cumulative probability function) của X cho trước Y được định nghĩa:

{: .highlight }
$$
F_{X|Y}(x|y) = P\{X \le x | Y = y\} = \sum_{a \le x} p_{X|Y}(a|y)
$$

*Trong đó $$Y = y$$ với $$y$$ là cố định, chỉ có giá trị của X là thay đổi.*

Tương tự, ta có **kỳ vọng có điều kiện** (conditional expectation):

{: .highlight }
$$
E[X | Y = y] = \sum xP\{X = x | Y = y\} = \sum_x xp_{X|Y}(x|y)
$$

Ví dụ: Cho bảng xác suất đồng thời của biến X, Y. Tìm:

|     |Y=1   |Y=2   |
|-----|------|------|
|X=1  | 0.2  | 0.4  |
|X=2  | 0.1  | 0.1  |
|X=3  | 0.05 | 0.05 |

a. Tính xác suất điều kiện PMF:
$$
P\{X=1 | Y = 2\}, P\{X=2 | Y = 2\}, P\{X=3 | Y = 2\}
$$

b. Tính xác suất điều kiện CDF:
$$
P\{X < 3 | Y = 1\}
$$

c. Tính kỳ vọng: 
$$
E[X|Y=2]
$$

Trả lời:

a.
$$
P\{X=1 | Y = 2\} = \frac{P\{X = 1, Y = 2\}}{P\{Y = 2\}} = \frac{0.4}{0.55} \approx 0.72
$$. 

Tính tương tự cho các x còn lại. Một điều cần lưu ý là **tổng của $$P\{X=1 \vert Y = 2\}, P\{X=2 \vert Y = 2\}, P\{X=3 \vert Y = 2\}$$ phải bằng 1.**

b. 
$$
\begin{aligned}
& P\{X \le 2 | Y = 1\} = P\{X=1 | Y=1\} + P\{X=2 | Y=1\} \\
& = 0.2 + 0.1 = 0.3
\end{aligned}
$$

c.
$$
\begin{aligned}
& E[X|Y=2] = 1 \cdot p_{X|Y}(1|2) + 2 \cdot p_{X|Y}(2|2) + 3 \cdot p_{X|Y}(3|2) \\
& = 1 \cdot 0.4 + 2 \cdot 0.1 + 3 \cdot 0.05 = 0.75
\end{aligned}
$$

# Continuous cases

Cho X, Y là các biến ngẫu nhiên liên tục có hàm mật độ xác suất đồng thời $$f(x, y)$$, **hàm mật độ xác suất có điều kiện** (conditional probability density function) của X được định nghĩa như sau:

{: .highlight }
$$
f_{X|Y}(x|y) = \frac{f(x, y)}{f_Y(y)}
$$

với xác suất biên $$f_Y(y) > 0$$ cho mọi giá trị của $$y$$.

**Hàm xác suất tích luỹ có điều kiện** (conditional cumulative probability function) của X cho trước Y được định nghĩa:

{: .highlight }
$$
F_{X|Y}(x | y) = P\{X \le x | Y = y\} = \int_{-\infty}^x f_{X|Y}(a|y)da
$$

*Trong đó, $$Y = y$$ là cố định, chỉ có giá trị của X là thay đổi*.

Tương tự, ta có **kỳ vọng có điều kiện** (conditional expectation):

{: .highlight }
$$
E[X | Y = y] = \int_{-\infty}^{\infty} xf_{X|Y}(x|y)dx
$$

Ví dụ:

Cho hàm xác suất đồng thời X, Y:

$$
f(x,y) = \begin{cases}
6xy(2 - x - y) \text{ , } 0 < x < 1, 0 < y < 1\\
0 \text{ , otherwise}
\end{cases}
$$

a. Tính $$f_{X \vert Y}(x \vert \frac{1}{2})$$.
b. Tính $$E[X \vert Y = \frac{1}{2}]$$.

Đáp án:

Ta có: 
$$
\begin{aligned}
f_{X|Y}(x|\frac{1}{2}) = \frac{f(x, \frac{1}{2})}{f_Y(\frac{1}{2})}
\end{aligned}
$$

- Tìm $$f(x , \frac{1}{2})$$:

$$
f(x , \frac{1}{2}) = 6x\frac{1}{2}(2 - x - \frac{1}{2}) = \frac{9x}{2} - 3x^2
$$

- Tìm $$f_Y(\frac{1}{2})$$ (xem lại [phân phối đồng thời của biến liên tục](https://nlamduy.github.io/docs/stochastic-process/random-variables/expectation-variance.html#join-probability-distribution)):

$$
\begin{aligned}
f_Y(\frac{1}{2}) & = \int_{-\infty}^{\infty}f(x, \frac{1}{2})dx \\
& = \int_0^1 (\frac{9x}{2} - 3x^2)dx \\
& = \left[ \frac{9}{2} \cdot \frac{x^2}{2} - 3 \cdot \frac{x^3}{3} \right]^1_0 \\
& = \frac{5}{4}
\end{aligned}
$$

Như vậy: $$\displaystyle f_{X \vert Y}(x \vert \frac{1}{2}) = \frac{4(\frac{9x}{2} - 3x^2)}{5}$$

Giá trị kỳ vọng:

$$
\begin{aligned}
E[X | Y = \frac{1}{2}] & = \int_{-\infty}^{\infty} xf_{X|Y}(x|\frac{1}{2})dx\\
& = \int_0^1 [x (\frac{4(\frac{9x}{2} - 3x^2)}{5})]dx \\
& =\int_0^1 (\frac{18x^2}{5} - \frac{12x^3}{5})dx \\
& = \left[ \frac{18}{5} \cdot \frac{x^3}{3} - \frac{12}{5} \cdot \frac{x^4}{4} \right]^1_0 \\
& = \frac{9}{50}
\end{aligned}
$$

# Computing expectations by conditioning

**Việc tính kỳ vọng của biến X mà điều kiện hoá trên một biến Y là một kỹ thuật rất hữu ích**. Giả sử ta muốn tính trung bình của X nhưng ta không biết xác suất biên của X. Tuy nhiên, nếu ta có được một liên hệ giữa biến X và Y, ta sẽ tính được ước lượng tốt nhất của X theo từng giá trị $$Y = y$$. Chẳng hạn, ta có $$y = \{1, 2, 3\}$$, thì với mỗi giá trị của y:

$$
\begin{aligned}
& E[X | Y = 1] \leftarrow y = 1 \\
& E[X | Y = 2] \leftarrow y = 2 \\
& E[X | Y = 3] \leftarrow y = 3 \\
\end{aligned}
$$

Ta nói, $$E[X \vert Y = 1]$$ là ước lượng tốt nhất trung bình của X với điều kiện $$y = 1$$. Quay trở lại ví dụ ở phần trước, ta biết $$E[X \vert Y = \frac{1}{2}] = \frac{9}{50}$$, thì $$\frac{9}{50}$$ là ước lượng trung bình tốt nhất của X với điều kiện $$y = \frac{1}{2}$$. Về mặt ý nghĩa, nếu ta thực hiện:

$$
\begin{aligned}
& E[X | Y = 1]P(Y = 1) \leftarrow y = 1 \\
& E[X | Y = 2]P(Y = 2) \leftarrow y = 2 \\
& E[X | Y = 3]P(Y = 3) \leftarrow y = 3 \\
\end{aligned}
$$

thì $$\sum_{y=1}^3 E[X \vert Y=y]P(Y=y) = E[X]$$ là ước lượng trung bình không điều kiện của X.

Phương pháp này được gọi là **điều kiện hoá** (hay **tower property**) với công thức tổng quát:

{: .highlight}
$$
\begin{aligned}
E[X] & = E[E[X | Y]] \\
& = \begin{cases}
    \sum_y E[X | Y = y]P\{Y = y\} \text{ , if Y is a discrete rv} \\
    \int_{-\infty}^{\infty} E[X | Y = y]f_Y(y)dy \text{ , if Y is a continuous rv}
\end{cases}
\end{aligned}
$$

Kỹ thuật này rất hữu ích, đặc biệt với trường hợp chúng ta không thể tính trực tiếp $$E[X]$$, nhưng lại tìm được mối quan hệ của X với một biến ngẫu nhiên khác.

Ví dụ:

Một danh mục bảo hiểm có 3 loại rủi ro: thấp (G), trung bình (N) và cao (B). Số tiền đền bù khi có yêu cầu từ khách hàng tuân theo [phân phối mũ](https://nlamduy.github.io/docs/stochastic-process/random-variables/continuous-random-variable.html#exponential-random-variable) với tham số $$\lambda$$ phụ thuộc vào loại rủi ro. Cụ thể, $$\lambda_G = 0.1, \lambda_N = 0.05, \lambda_B = 0.02$$. Cho rằng danh mục có 60% khách hàng là rủi ro thấp, 30% rủi ro trung bình và 10% là rủi ro cao:
a. Tìm số tiền đền bù trung bình nếu chọn ngẫu nhiên từ danh mục. 

Trả lời:
Gọi X là biến ngẫu nhiên đại diện số tiền đền bù, Y là biến ngẫu nhiên đại diện cho mức độ rủi ro. 

$$
\begin{aligned}
E[X] & = E[E[X|Y]] \\
& = E[X|Y=G]P(Y=G) \\
& = E[X|Y=N]P(Y=N) \\
& = E[X|Y=B]P(Y=B) \\
\end{aligned}
$$

Từ dữ kiện đề bài ta có $$P(Y=G) = 0.6, P(Y=N) = 0.3, P(Y=B)=0.1$$. Ta biết, [kỳ vọng của phân phối mũ](https://nlamduy.github.io/docs/stochastic-process/random-variables/expectation-variance.html) là $$E[X] = \frac{1}{\lambda}$$. Mà kỳ vọng của X khi Y xảy ra tuân theo phân phối mũ, do đó:

- $$E[X | Y = G] = \frac{1}{\lambda_G} = 10$$
- $$E[X | Y = N] = \frac{1}{\lambda_N} = 20$$
- $$E[X | Y = B] = \frac{1}{\lambda_B} = 50$$

Như vậy, nếu chọn ngẫu nhiên một hồ sơ đền bù từ danh mục bảo hiểm, thì số tiền đền bù trung bình là: 

$$
E[X] = 10 \ cdot 0.6 + 20 \cdot 0.3 + 50 \cdot 0.1 = 17
$$


# Computing variances by conditiong

Để tính phương sai với phương pháp điều kiện hoá, chúng ta có 2 phương pháp như bên dưới:

**Cách 1 (Phương sai cổ điển):**

{: .highlight}
$$
Var(X) = E[X^2] - (E[X^2]) = E[E[X^2 | Y]] - (E[E[X | Y]])^2
$$

**Cách 2 (Phương sai toàn phần):**

{: .highlight}
$$
Var(X) = E[Var(X | Y)] + Var(E[X | Y])
$$

Trong đó, $$E[Var(X \vert Y)]$$ là phương sai giải thích được và $$Var(E[X \vert Y])$$ là phương sai không giải thích được.

# References

Eberly College of Science. (n.d.-b). 20.2 - Conditional distributions for continuous random variables \| STAT 414. PennState: Statistics Online Courses. https://online.stat.psu.edu/stat414/lesson/20/20.2

Nguyen Huu, Thai (n.d.). Lecture: Conditional Probability and Conditional Expectation. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.