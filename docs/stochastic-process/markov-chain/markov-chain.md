---
layout: default
math: mathjax
title: Markov Chain
parent: Stochastic Process
# has_children: true
nav_order: 4
---

# Markov Chain
{: .no_toc }

Xích Markov là một hệ thống toán học diễn ra các chuyển đổi từ trạng thái này sang trạng thái khác, trong một số lượng hữu hạn hoặc đếm được các trạng thái có thể. Đây là một quá trình ngẫu nhiên nơi trạng thái tương lai chỉ phụ thuộc vào trạng thái hiện tại và không phụ thuộc vào chuỗi các sự kiện đã xảy ra trước đó. Tính chất này được gọi là **“không nhớ” và là một đặc điểm chính của xích Markov**.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


# Stochastic process

Một quá trình ngẫu nhiên là họ của biến ngẫu nhiên $$\{X_t : t \in T\}$$ nhận giá trị trong không gian trạng thái, trong đó:
- Cho mỗi $$t \in T, X_t$$ là một biến ngẫu nhiên.
- Chỉ số $$T$$ và không gian trạng thái (state space) có thể là liên tục hoặc rời rạc.
- Cho $$T = \{0,1,2,3,4,...,\}$$ (rời rạc) hoặc $$T = \mathbb{R}, \mathbb{R^+}, \mathbb{R^2}, \mathbb{R^3}$$ (liên tục).

![markov_eg2](/assets/img/stochastic-process/markov_eg2.png)

Một số trường hợp:

- Thời gian, trạng thái rời rạc: Xích Markov
- Thời gian rời rạc, trạng thái liên tục: Kalma Filter
- Thời gian liên tục, trạng thái rời rạc: Birth and Death Process
- Thời gian, trạng thái liên tục: Brownian Motion

# Markov assumption

**Đặt vấn đề:** Cho X là một quá trình ngẫu nhiên rời rạc với $$t = \{0, 1, ..., n\}$$ với $$n$$ là thời điểm hiện tại. Giá trị của biến ngẫu nhiên trong quá khứ $$X_0, ..., X_{n - 1}$$ và hiện tại $$X_n$$ cho chúng ta biết gì về phân phối của $$X_{n + 1}$$?

![markov_eg3](/assets/img/stochastic-process/markov_eg3.png)

{: .important }
**Những gì xảy ra trong tương lai chỉ phụ thuộc vào hiện tại:**
$$
P\{X_{n + 1} = j \vert X_n = i, X_{n - 1} = a\} = P\{X_{n + 1} = j \vert X_n = i\}
$$

# Transition probability matrix

Nếu $$P\{X_{n + 1} = j \vert X_n = i\} = P_{ij}$$ không phụ thuộc vào $$n$$ thì quá trình $$X_n : n = 0, 1, 2, ...$$ được gọi là xích Markov dừng (stationary). Trong đó, $$P_{ij}$$ được gọi là xác suất chuyển (transition probabilities) từ trạng thái $$i$$ sang trạng thái $$j$$.

Ma trận xác suất chuyển:

$$
P = \begin{bmatrix}
P_{00} & P_{01} & P_{02} & ... & P_{0j} & ... \\
P_{10} & P_{11} & P_{12} & ... & P_{1j} & ... \\
... & ... & ... & ... & ... & ... \\
P_{i0} & P_{i1} & P_{i2} & ... & P_{ij} & ... \\
... & ... & ... & ... & ... & ... 
\end{bmatrix}
$$

{: .note }
> Xác suất chuyển $$P_{ij}$$ thoả mãn những điều sau:
> - Xác suất chuyển không âm $$P_{ij} \ge 0$$ cho mọi $$i, j$$.
> - Tổng xác suất (theo dòng) $$\sum_j P_{ij} = 1$$ cho mọi $$i$$.

{: .highlight }
**Quy tắc đọc ma trận xác suất chuyển là dọc từ dòng (trạng thái tại $$n$$) sang cột (trạng thái tại $$n + 1$$).**

Ví dụ 1:

Cho xích Markov $$\{X_0, X_1, X_2, ... \}$$ mô tả thời tiết với 3 trạng thái $$S = \{Sunny, Cloudy, Rainny\}$$ và xác suất chuyển như sau:

![markov_eg4](/assets/img/stochastic-process/markov_eg4.png)

Xác định xác suất chuyển từ trạng thái Sunny sang Sunny, Sunny sang Rainny, Rainny sang Cloudy, Rainny sang Sunny.

Đáp án:

$$
\begin{align*}
P\{X_{n + 1} = Sunny \vert X_n = Sunny\} = 0.2\\
P\{X_{n + 1} = Rainny \vert X_n = Sunny\} = 0.4\\
P\{X_{n + 1} = Cloudy \vert X_n = Rainny\} = 0.7\\
P\{X_{n + 1} = Sunny \vert X_n = Rainny\} = 0.0
\end{align*}
$$

Diễn đạt bằng lời như sau: Giả sử $$n$$ là ngày hôm nay thì, xác suất ngày hôm nay ($$X_n$$) là Sunny và ngay mai ($$X_{n + 1}$$) tiếp tục Sunny là 0.2. Hoặc, xác suất ngày hôm nay ($$X_n$$) là Sunny và ngay mai ($$X_{n + 1}$$) Rainny là 0.2.

Ngoài ra, còn có thể biểu diễn ma trận xác suất chuyển bằng đồ thị bên dưới:

![markov_eg5](/assets/img/stochastic-process/markov_eg5.png)

Ví dụ 2:

Cho xích Markov $$\{X_0, X_1, ...\}$$ gồm 3 trạng thái $$S = \{0, 1, 2\}$$ với ma trận xác suất chuyển:

![markov_eg6](/assets/img/stochastic-process/markov_eg6.png)

và xác suất phân phối khởi đầu (xuất phát của xích Markov) $$P\{X_0 = 0\} = 0.3, P\{X_0 = 1\} = 0.4$$, hoặc $$P\{X_0 = 2\} = 0.3$$. Nói cách khác ở thời điểm bắt đầu ($$t = 0$$), X có thể nhận 1 trong 3 trạng thái với xác suất tương ứng như trên. 

![markov_eg7](/assets/img/stochastic-process/markov_eg7.png)

Tính:

1. $$P(X_0 = 0, X_1 = 2, X_2 = 2)$$
2. $$P(X_1 = 1, X_2 = 1 \vert X_0 = 0)$$

Đáp án:

Để tính được các xác suất trên, cần sử dụng [xác suất có điều kiện](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#conditional-probabilities).

- Tính $$P(X_0 = 0, X_1 = 2, X_2 = 2)$$:

$$
\begin{aligned}
& P(X_0 = 0, X_1 = 2, X_2 = 2) \\
& = P(X_2 = 2 | X_0 = 0, X_1 = 1)P(X_0 = 0, X_1 = 1) \\
& = P(X_2 = 2 | X_1 = 1)P(X_1 = 1 | X_0 = 0)P(X_0 = 0) \\
& = 0 \cdot 0.2 \cdot 0.3 = 0
\end{aligned}
$$

Ở đây, $$P(X_2 = 2 \vert X_0 = 0, X_1 = 1)$$ có thể bằng $$P(X_2 = 2 \vert X_1 = 1)$$ vì giả định của xích Markov là những gì xảy ra ở tương lai ($$X_2$$) chỉ phụ thuộc vào hiện tại ($$X_1$$), nên ta có thể bỏ qua quá khứ $$X_0$$ trong trường hợp này.

- Tính $$P(X_1 = 1, X_2 = 1 \vert X_0 = 0)$$:

$$
\begin{aligned}
& P(X_1 = 1, X_2 = 1 | X_0 = 0) \\
& = P(X_2 = 1 | X_1 = 1, X_0 = 0)P(X_1 = 1 | X_0 = 0) \\
& = P(X_2 = 1| X_1 = 1)P(X_1 = 1 | X_0 = 0) \\
& = 0.1 \cdot 0.2 = 0.02
\end{aligned}
$$

Từ ví dụ này, **ta có thể mở rộng thêm phần xác suất có điều kiện** cho xích Markov:

{: .new }
$$
\begin{aligned}
P(A,B|C) & = \frac{P(A,B,C)}{P(C)} \\
& = \frac{P(A|B,C)P(B,C)}{P(C)} \\
& = P(A|B,C)P(B|C) \\
& = P(A,B|C) = P(A|B,C)P(B|C)
\end{aligned}
$$

# Chapman-Kolmogorov equation

Cho $$P_{ij}^{(n)}$$ là xác suất trạng thái $$i$$ chuyển sang trạng thái $$j$$ sau $$n$$ bước chuyển, tức là:

{: .important }
$$
P_{ij}^{(n)} = P\{X_{n + 1} = j \vert X_k = i\} \text{ , } n \ge 0, i, j \ge 0
$$

Thì phương trình Chapman-Kolmogorov để tính xác suất chuyển sau $$n$$ bước là:

{: .important }
$$
P_{ij}^{(n + m)} = \sum_{k = 0}^{\infty} P_{ik}^{(n)} P_{kj}^{(m)} \text{ for all } n, m \ge 0 \text{ , all } i, j
$$

Ví dụ 1:

Cho xích Markov với 3 trạng thái $$\{1, 2, 3\}$$ và ma trận xác suất chuyển:

$$ 
P = \begin{bmatrix}
0.1 & 0.3 & 0.6 \\
0.4 & 0.2 & 0.4 \\
0.3 & 0.3 & 0.4 
\end{bmatrix}  
$$

Tính xác suất chuyển $$P\{X_2 = 3 \vert X_0 = 2\}$$.

Đáp án:

Áp dụng công thức [xác suất toàn phần](https://nlamduy.github.io/docs/stochastic-process/probability-theory/probability.html#total-probability-law):

$$
\begin{aligned}
& P\{X_2 = 3 | X_0 = 2\} \\
& = P\{X_2 = 3 | X_1 = 1, X_0 = 2\}P\{X_1 = 1 | X_0 = 2\} \\
& + P\{X_2 = 3 | X_1 = 2, X_0 = 2\}P\{X_1 = 2 | X_0 = 2\} \\
& + P\{X_2 = 3 | X_1 = 3, X_0 = 2\}P\{X_1 = 3 | X_0 = 2\} \\
& = 0.6 \cdot 0.4 + 0.4 \cdot 0.2 + 0.4 \cdot 0.4 = 0.48
\end{aligned}
$$

Từ công thức trên có thể viết thành:

$$
P\{X_2 = 3 | X_0 = 2\} = P_{21}P_{13} + P_{22}P_{23} + P_{23}P_{33}
$$

Trực quan hơn:

![markov_eg8](/assets/img/stochastic-process/markov_eg8.png)

Điều này cũng có thể đạt được bằng cách luỹ thừa ma trận xác suất chuyển lên 2 lần:

```python
from numpy.linalg import matrix_power
import numpy as np

P = np.array([[0.1, 0.3, 0.6], [0.4, 0.2, .4], [0.3, 0.3, 0.4]])

#Ma trận xác suất chuyển sau 2 bước
matrix_power(P, 2)
```
```
array([[0.31, 0.27, 0.42],
       [0.24, 0.28, 0.48],
       [0.27, 0.27, 0.46]])
```

Kết quả từ dòng 2, cột 3 là $$P_{23} = 0.48$$.

Ví dụ 2:

Cho ma trận xác suất chuyển với 2 trạng thái như sau:

$$
P = \begin{bmatrix}
0.7 & 0.3 \\
0.4 & 0.6
\end{bmatrix}  
$$

Tính xác suất chuyển $$P_{00}$$ sau 4 bước.

Đáp án:

```python
from numpy.linalg import matrix_power
import numpy as np

P = np.array([[0.7, 0.3], [0.4, 0.6]])

#Ma trận xác suất chuyển sau 4 bước
matrix_power(P, 4)
```
```
array([[0.5749, 0.4251],
       [0.5668, 0.4332]])
```
Như vậy, $$P_{00}^{(4)} = 0.5749$$.

# Classification of states

Các trạng thái trong một xích Markov có thể được phân loại thành thường xuyên (recurrent), tạm thời (transient) và hấp thụ (absorbing) dựa vào khả năng tiếp cận (accessible), liên lạc (communicate) của chúng.

{: .note }
1. **Khả năng tiếp cận:** Một trạng thái $$j$$ được cho là có thể tiếp cận từ trạng thái $$i$$, được ký hiệu là $$i \rightarrow j$$, nếu có một xác suất chuyển từ $$i$$ sang $$j$$ trong một số bước hữu hạn, lớn hơn 0.
2. **Khả năng liên lạc:** Các trạng thái $$i$$ và $$j$$ liên lạc với nhau nếu $$i$$ có thể tiếp cận từ $$j$$ và $$j$$ có thể tiếp cận từ $$i$$, được ký hiệu là $$i \leftrightarrow j$$.
3. **Trạng thái thường xuyên:** Một trạng thái là thường xuyên nếu xuất phát từ một trạng thái $$i$$ và sẽ quay lại trạng thái $$i$$ vô hạn lần với xác suất $$P \{ \text{ever re-enter } i \vert X_0 = i \} = 1$$.
4. **Trạng thái tạm thời:** Một trạng thái là tạm thời nếu xuất phát từ một trạng thái $$i$$ và sẽ quay lại trạng thái $$i$$ hữu hạn lần với xác suất $$P\{ \text{ever re-enter } i \vert X_0 = i \} < 1$$.
5. **Trạng thái hấp thụ:** Một trạng thái là hấp thụ nếu một khi đã vào, không thể rời khỏi trạng thái đó.

Ví dụ 1:

Cho ma trận xác suất chuyển với 3 trạng thái {1, 2, 3} như sau:

$$
P = \begin{bmatrix}
0.1 & 0.2 & 0.7 \\
0.4 & 0.4 & 0.2 \\
0   & 0   & 1
\end{bmatrix}  
$$

![markov_eg9](/assets/img/stochastic-process/markov_eg9.png)

Có thể rút ra những nhận xét sau:
- Trạng thái 1 có thể tiếp cận từ 2, 2 có thể tiếp cận được từ 1, 3 có thể tiếp cận được từ 1 và 2.
- Trạng thái 1 và 2 có khả năng liên lạc với nhau.
- Trạng thái 3 là một trạng thái hấp thụ vì khi đã vào thì không thể thoát ra.

{: .highlight }
- Hai trạng thái nếu liên lạc được với nhau thì cùng một lớp (class) và có tính chất tương tự nhau.
- Một xích Markov được gọi là tối giản (irreducible) nếu chi có một lớp.

Ví dụ 2:

Cho ma trận xác suất chuyển với 3 trạng thái {1, 2, 3} như sau:

$$
P = \begin{bmatrix}
1/2 & 1/2 & 0 \\
1/2 & 1/4 & 1/4 \\
0   & 1/3 & 2/3
\end{bmatrix}  
$$

Trạng thái 3 có thể tiếp cận được từ trạng thái 1 hay không?

Đáp án:

Trạng thái 3 không thể tiếp cận trực tiếp từ trạng thái 1, nhưng có thể sau 2 bước. Cụ thể, trạng thái 1 chuyển sang trạng thái 2 và từ trạng thái 2 chuyển sang trạng thái 3. Xác suất $$P_{13}^{(2)} = 0.125$$.

```python
from numpy.linalg import matrix_power
import numpy as np

P = np.array([[0.5, 0.5, 0], [0.5, 0.25, 0.25], [0, 1/3, 2/3]])

#Ma trận xác suất chuyển sau 2 bước
matrix_power(P, 2)
```
```
array([[0.5       , 0.375     , 0.125     ],
       [0.375     , 0.39583333, 0.22916667],
       [0.16666667, 0.30555556, 0.52777778]])
```

{: .highlight }
Trạng thái $$j$$ có thể tiếp cận được từ trạng thái $$i$$ sau $$n$$ bước.



# References

Nguyen Huu, Thai (n.d.). Lecture: Introduction to Markov Chain. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

