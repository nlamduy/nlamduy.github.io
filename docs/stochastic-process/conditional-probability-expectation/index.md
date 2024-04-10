---
layout: default
title: Conditional Probability and Conditional Expectation
parent: Stochastic Process
# has_children: true
nav_order: 3
---

# Conditional Probability and Conditional Expectation
{: .no_toc }

**Xác suất có điều kiện** là khả năng xảy ra của một sự kiện, giả sử rằng một sự kiện khác đã xảy ra. Đây là cách để tính toán xác suất mà có tính đến thông tin hiện có. **Kỳ vọng có điều kiện** là giá trị kỳ vọng của một biến ngẫu nhiên khi một điều kiện nhất định được thỏa mãn. Nó giống như lấy trung bình của một tập hợp các số, nhưng chỉ những số nào đáp ứng một tiêu chí cụ thể.

Xác suất có điều kiện đã được giới thiệu ở [đây](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities). Trong phần này sẽ được trình bày chi tiết hơn.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Discrete case

Cho X, Y là các biến ngẫu nhiên rời rạc với hàm xác suất đồng thời $$p(x, y)$$, **hàm xác suất khối có điều kiện** (conditional probability mass function) của X với điều kiện Y đã xảy ra ($$Y = y$$) được định nghĩa:

{: .highlight }
$$
p_{X|Y}(x|y) = P\{X = x | Y = y\} = \frac{P\{X = x, Y = y\}}{P\{Y = y\}} = \frac{p(x, y)}{p_Y(y)}
$$

cho tất cả giá trị của $$y$$ với $$P\{Y = y\} > 0$$. 

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
$$. Tính tương tự cho các x còn lại. Một điều cần lưu ý là **tổng của $$P\{X=1 | Y = 2\}, P\{X=2 | Y = 2\}, P\{X=3 | Y = 2\}$$ phải bằng 1.**

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
