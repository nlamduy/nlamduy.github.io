---
layout: default
math: mathjax
title: Probability
parent: Probability Theory
grand_parent: Stochastic Process
nav_order: 2
---

# Probability
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


**Các nguyên tắc cơ bản** khi tính xác suất:

{: .highlight }

- Xác suất của không gian mẫu: $$P(\Omega) = 1$$

- Xác suất của một sự kiện $$E$$ bất kỳ: $$0 \le P(E) \le 1$$

- Tổng xác suất các biến cố xung khắc $$E_i, i=1,2,3...$$: $$P\left(\bigcup_i E_i\right) = {\displaystyle \sum_i P(E_i)}$$


**Nguyên tắc thứ 3 là quan trọng nhất**.

# Addition law

**Xác suất cộng** của 2 sự kiện:

{: .highlight }

$$
P(E_1 \cup E_2) = P(E_1) + P(E_2) - P(E_1 \cap E_2)
$$


Nếu $$E_1$$ và $$E_2$$ là **hai biến cố xung khắc**:

{: .highlight }

$$
P(E_1 \cup E_2) = P(E_1) + P(E_2)
$$


Ví dụ:

Một loại thuốc có thông tin như sau:

- Xác suất 10% bị đau đầu (H).
- Xác suất 15% bị buồn nôn (N).
- Xác suất 5% bị cả hai tác dụng phụ.

Xác suất bị ít nhất một tác dụng phụ: $$P(H \cup N) = P(H) + P(N) - P(H \cap N) = 0.1 + 0.15 - 0.05 = 0.2$$

# Poincaré's theorem (inclusion-exclusion principle)

Định lý [Poincaré](https://vi.wikipedia.org/wiki/Henri_Poincaré) dùng để tính **xác suất cộng của $$n$$ biến cố**.

Ví dụ, tính xác suất của $$P(E_1 \cup E_2 \cup E_3)$$.

{: .highlight }

$$
\begin{aligned}
P(E_1 \cup E_2 \cup E_3) = P(E_1) + P(E_2) + P(E_3) - P(E_1 \cap E_2) \\
 - P(E_1 \cap E_3) - P(E_2 \cap E_3) + P(E_1 \cap E_2 \cap E_3)
\end{aligned}
$$


# Conditional probabilities

**Xác suất có điều kiện** của sự kiện $$E_1$$ khi $$E_2$$ đã xảy ra được tính:

{: .highlight }

$$
P(E_1|E_2) = \frac{P(E_1 \cap E_2)}{P(E_2)} 
$$


Ví dụ:

Xét tình trạng thăng cấp của viên chức cảnh sát trong hai năm qua:

|       | Male | Female | Total |
|-------|------|--------|-------|
| Yes   | 288  | 36     | 324   |
| No    | 627  | 204    | 876   |
| Total | 960  | 240    | 1200  |

Bảng xác suất đồng thời (join probability):

|       | Male | Female | Total |
|-------|------|--------|-------|
| Yes   | .24  | .03    | .27   |
| No    | .56  | .17    | .73   |
| Total | .80  | .20    | 1.00  |

Xác suất đồng thời được thể hiện trong phần giữa bảng. Các xác suất biên (marginal probabilities) được thể hiện ở phần lề của bảng.

Xác suất được thăng tiến nếu biết người đó là nữ: 

$$
P(Y | F) = \frac{P(Y \cap F)}{P(F)} = \frac{.03}{.20} = .15
$$

# Independent events

**Hai biến cố $$E_1$$ và $$E_2$$ là độc lập** nếu:

{: .highlight }

$$
P(E_1 | E_2) = P(E_1)
$$


Tuy nhiên, đối với **ba biến cố trở lên**, cần phải kiểm tra đồng thời:

{: .highlight }

$$
E_1 \perp E_2 \perp E_3  = \begin{cases}
P(E_1 | E_2) = P(E_1)\\
P(E_1 | E_3) = P(E_1)\\
P(E_2 | E_3) = P(E_2)\\
P(E_1 \cap E_2 \cap E_3) = P(E_1)P(E_2)P(E_3)
\end{cases}
$$


# Multiplication law

**Quy tắc nhân** được dùng để tính xác suất của phần giao hai biến cố:

{: .highlight }

$$
P(E_1 \cap E_2) = \begin{cases} 
P(E_1)P(E_2 | E_1) \\
P(E_2)P(E_1 | E_2)
\end{cases}
$$



Nếu **hai biến cố là độc lập**:

{: .highlight }

$$
P(E_1 \cap E_2) = P(E_1)P(E_2)
$$



# Total probability law

Quy tắc **xác suất toàn phần**:

{: .highlight }

$$
P(E_2) = P(E_2 \cap E_1) + P(E_2 \cap E_1^c) = P(E_1)P(E_2|E_1) + P(E_1^c)P(E_2|E_1^c)
$$



Trong đó, $$E_1^c$$ là phần bù của biến cố $$E_1$$.

Cho dãy $$\{A_1, A_2, A_3, ... A_i \}$$ là các sự kiện xung khắc và hợp của chúng bằng không gian mẫu $$\Omega$$, thì ta có một **cơ sở (base)** của $$\Omega$$.

Giả sử, dãy $$\{A_1, A_2, A_3\}$$ là cơ sở của $$\Omega$$. Cho sự kiện bất kỳ $$E$$ thuộc $$\Omega$$. Sử dụng xác suất toàn phần để tính $$E$$: $$P(E) = P(E \| A_1)P(A_1) + P(E \| A_2)P(A_2) + P(E \| A_3)P(A_3)$$

# Bayes' theorem 

Thông thường, chúng ta phân tích với mức xác suất ban đầu, hay xác suất tiên nghiệm (prior probability). Định lý Bayes cung cấp công thức để tính xác suất hậu nghiệm (posterior probability) khi có thông tin mới được bổ sung.

**Xác suất tiên nghiệm ---> Thông tin mới ---> Bayes ---> Xác suất hậu nghiệm**

## Two-event case

Cho hai biến cố $$A,B$$, áp dụng định lý Bayes:

{: .highlight }

$$
P(B | A) = \frac{P(A | B)P(B)}{P(A | B)P(B) + P(A | B^c)P(B^c)} = \frac{P(A | B)P(B)}{P(A)}
$$


## Case of n events

Cho dãy $$\{B_1, B_2,..., B_n\}$$ là cơ sở của $$\Omega$$.

{: .highlight }

$$
P(B_i | A) = \frac{P(A|B_i)P(B_i)}{P(A)} = \frac{P(A|B)P(B)}{\Sigma^n_{i=1} P(A|B_i)P(B_i)}
$$


## Tabular approach

Xét chất lượng cung cấp đơn hàng của hai nhà thầu A1 và A2:

|       | A1  | A2  | Total |
|-------|-----|-----|-------|
| Bad   | .02 | .05 | .07   |
| Good  | .63 | .30 | .93   |
| Total | .65 | .35 | 1.00  |


Áp dụng định lý Bayes với cách tiếp cận dạng bảng:

| (1)    | (2)        | (3)              | (4)          | (5)               |
|--------|------------|------------------|--------------|-------------------|
| Events | Prior Prob | Conditional Prob | Join Prob    | Posterior Prob    |
| $$A_i$$     | $$P(A_i)$$      | $$P(B \| A_i)$$         | $$P(Ai \cap B)$$      | $$P(A_i\|B)$$          |
| A1     | .65        | .02              | .0130        | .0130/.0305=.4262 |
| A2     | .35        | .05              | .0175        | .0175/.0305=.5738 |
|        | 1.00       |                  | P(B) = .0305 | 1.0000            |


# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Nguyen Huu, Thai. (n.d.). Lecture: Introduction to Probability Theory. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.