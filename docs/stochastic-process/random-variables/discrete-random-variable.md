---
layout: default
math: mathjax
title: Discrete Random Variables
parent: Random Variables
grand_parent: Stochastic Process
nav_order: 1
---

# Discrete Random Variables
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


Biến ngẫu nhiên rời rạc là tập hợp các **giá trị hữu hạn hoặc vô hạn đếm được** mà biến có thể nhận.

Ví dụ:

| Discrete Random Variable              | Description                                                                      | Possible Values                        |
|---------------------------------------|----------------------------------------------------------------------------------|----------------------------------------|
| Number of Heads in 10 Coin Flips      | Counts how many times a head appears when a fair coin is flipped 10 times.       | 0, 1, 2, ..., 10                       |
| Dice Roll Outcome                     | Represents the outcome of rolling a fair six-sided die.                          | 1, 2, 3, 4, 5, 6                       |


# Cumulative Distribution Function

Hàm phân phối tích luỹ **(CDF) đo xác suất của $$X \le x$$** của một biến ngẫu nhiên được định nghĩa:

{: .highlight }

$$
0 \le F_X(x) = P\{X \le x\} \le 1
$$


**Một số tính chất của hàm CDF:**

{: .highlight }

- $$F_X(x)$$ là một hàm không giảm (nondecreasing function)[^1] của x.
- $$\lim_{x \to \infty} F_X(x) = F(+\infty) = 1$$.
- $$\lim_{x \to -\infty} F_X(x) = F(-\infty) = 0$$.

# Probability mass function

Hàm khối xác suất **(PMF) đo xác suất tại một điểm cụ thể** của biến ngẫu nhiên rời rạc X. PMF được tính như sau:

{: .highlight }

$$
p_X(x) = P\{X = x\} = \{\omega \in \Omega: X(\omega) = x\}
$$


**Một số đặc điểm của hàm PMF:**

- Tập support (tất cả giá trị có thể nhận được) của X là đếm được nên: $$p_X(x_i) > 0 \text{ với } i = 1,2,...$$
- Tổng của tất cả các mass (xác suất từng giá trị của X): $$\Sigma^{\infty}_{i=1}p_X(x_i) = 1$$
- Hàm CDF được tính: $$F_X(x) = \Sigma_{\text{ all } x_i \le x}p_X(x)$$

Ví dụ:

Tung 3 đồng xu. Cho X là số lần được mặt sấp. Tìm hàm khối xác suất (PMF) và hàm xác suất tích luỹ (CDF).

Ta có:

- Không gian mẫu $$\Omega$$ = {HHH, HHT, HTH, THH, HTT, THT, TTH, TTT}
- Tất cả giá trị có thể nhận được (support) của X là: X = {0, 1, 2, 3}.

Tính:

PMF: $$p_X(x) = P\{X = x\} = \{\omega \in \Omega: X(\omega) = x\}$$

$$p_X(x) = \begin{cases} 
P\{X=0\} = 1/8 \\
P\{X=1\} = 3/8 \\
P\{X=2\} = 3/8 \\
P\{X=3\} = 1/8
\end{cases}$$

CDF: $$F_X(x)=P\{X \le x\}$$

$$F_X(x) = \begin{cases} 
0 \text{ , } x \le 0 \\
P\{X = 0\} = 1/8 \text{ , } 0 \le x < 1 \\
P\{X = 0\} + P\{X=1\}= 1/8 + 3/8 = 4/8 \text{ , } 1 \le x < 2 \\
P\{X = 0\} + P\{X=1\} + P\{X=2\} = 4/8 + 3/8 = 7/8 \text{ , } 2 \le x < 3 \\
1 \text{ , } x \ge 3
\end{cases}$$

# Bernoulli and Binomial random variable

Phân phối nhị thức (binomial distribution) được sử dụng để tính **xác suất số lần thành công $$i$$ trong $$n$$ phép thử**.

**Tính chất phép thử nhị nhức (binomial):**

{: .highlight }

1. Dãy gồm $$n$$ phép thử giống nhau.
2. Mỗi phép thử chỉ có 2 kết quả: thành công, thất bại.
3. Xác suất thành công $$p$$ không đổi qua các phép thử. Xác suất thất bại là $$1 - p$$.
4. Các phép thử độc lập với nhau. 

Các tính chất 2, 3, 4 thuộc quá trình [Bernoulli](https://vi.wikipedia.org/wiki/Jacob_Bernoulli). Nếu tính chất 1 thỏa mãn, ta có phép thử nhị thức.

Gọi X là biến nhị thức có tham số $$(n, p)$$ với $$n$$ là số lượng phép thử, xác suất thành công $$p$$ không đổi ở mỗi phép thử. **Hàm khối xác suất (PMF)** được trình bày như sau:

{: .highlight }

$$
p_X(i) = \left( 
\begin{array}{c} 
n \\ 
i 
\end{array} \right) p^i (1-p)^{n-i} = \frac{n!}{(n - i)!i!} p^i (1 - p)^{n-i} \text{ , } i =0, 1, ... n
$$


Ví dụ: Tung 4 đồng xu. Nếu kết quả mỗi phép thử (tung 1 đồng xu) là độc lập, tính xác suất có 2 mặt ngửa.

Gọi X là số lần mặt ngửa, với xác suất thành công (mặt ngửa) $$p = \frac{1}{2}$$ cho mỗi lần thử.

$$
p_X(2) = \left( 
\begin{array}{c} 
4 \\ 
2 
\end{array} \right) p^2 (1-p)^{4-2} = \frac{4!}{(4 - 2)!2!} p^2 (1 - p)^{4-2} = \frac{3}{8}
$$

# Geometric random variable

Phân phối hình học (gemotric distribution) được sử dụng để tính **xác suất của $$n$$ phép thử đến khi thành công**. 

Gọi X là số lần thử đến khi thành công, thì X là một biến hình học với tham số $$p$$, với $$p$$ là xác suất thành công không đổi ở mỗi phép thử. **Hàm khối xác suất (PMF)** được trình bày như sau:

{: .highlight }

$$
p(n) = P \{ X=n \} = (1-p)^{n-1}p \text{ , n = 1, 2, ...}
$$


Ví dụ: Cho X là biến hình học đại diện cho số lần tung đồng xu đến khi xuất hiện mặt ngửa. Tính xác suất thành công sau 1, 2 và 3 lần thử, biết xác suất mặt ngửa  $$p = 0.5$$ là không đổi qua các phép thử.

- $$p(1) = P \{ X=1 \} = (1-0.5)^{1-1}0.5 = 0.5$$
- $$p(2) = P \{ X=2 \} = (1-0.5)^{2-1}0.5 = 0.25$$
- $$p(3) = P \{ X=3 \} = (1-0.5)^{3-1}0.5 = 0.125$$

Biến hình học có tính **không nhớ (memoryless)**. Đây là biến ngẫu nhiên rời rạc **duy nhất** có tính chất này. Cụ thể, nếu đã thực hiện phép thử $$n$$ lần, thì xác suất thử thêm $$m$$ lần nữa cho đến khi thành công không bị ảnh hưởng bởi $$n$$ lần phép thử trước đó:

{: .highlight }

$$
P\{ X > n + m | X > n \} = P\{ X > m \} \text{ , } \forall m,n \in \mathbb{N}
$$

# Negative binomial random variable

Phân phối nhị thức âm là một dạng mở rộng của phân phối hình học, được dùng để tính **xác suất của lần thành công thứ $$r^{th}$$ trong $$n$$ phép thử**. Cho X là biến nhị thức âm, **hàm khối xác suất (PMF)** được trình bày như sau:

{: .highlight }

$$
p(n) = P \{ X=n \} = \binom{n - 1}{r - 1}(1-p)^{n-r}p^r \text{ , n = r, r+1, r+2, ...}
$$


Ví dụ: Tung 1 đồng xu 10 lần với xác suất mặt ngửa không đổi $$p = 0.5$$.

# Poisson random variable

Phân phối Poisson (poisson distribution) được sử dụng để tính **xác suất số lần xảy ra trong một khoảng không gian, hoặc thời gian xác định**. Biến ngẫu nhiên cần quan tâm có thể là số khách hàng đến quầy giao dịch trong 1 giờ, số ổ gà trên 1km đường.

Tính chất của phép thử [Poisson](https://vi.wikipedia.org/wiki/Siméon-Denis_Poisson):

{: .highlight }

1. Đối với hai khoảng thời gian, hoặc không gian bất kỳ có độ dài như nhau thì xác suất xảy ra bằng nhau.
2. Việc xảy ra hay không xảy ra trong khoảng này thì độc lập với việc xảy ra hay không xảy ra trong khoảng khác.

Gọi X là biến ngẫu nhiên cần quan tâm với số lần xảy ra $$i$$ nhận các giá trị 0, 1, 2, ... X là biến Poisson có tham số $$\lambda$$, với $$\lambda > 0$$. **Hàm khối xác suất (PMF)** được trình bày như sau:

{: .highlight }

$$
p(i) = P\{ X = i\} = e^{-\lambda}\frac{\lambda^i}{i!} \text{ , } i = 0, 1, ...
$$

*Trong đó: $$e \approx 2.71828$$*

Ví dụ 1: Số lỗi đánh máy trên một trang sách tuân theo phân phối Poisson có tham số $$\lambda = 1$$. Tính xác suất có **ít nhất** một lỗi trên trang đó.

$$P\{ X \ge 1 \} = 1 - P\{ X < 1 \} = 1 - e^{-1}\frac{1^0}{0!} \approx 0.6321$$

Ví dụ 2: Số lượng khách hàng đến quầy giao dịch tuân theo phân phối Poisson. Biết rằng trung bình có 10 khách đến trong 15 phút. Tính xác suất có đúng 5 khách trong 15 phút.

$$P\{ X=5 \} = e^{-10}\frac{10^5}{5!} \approx 0.0378$$

Ví dụ 3: Từ ví dụ 2 ở trên. Tính xác suất có đúng 1 khách đến trong 3 phút.

$$\lambda = \frac{10}{15} \cdot 3 = 2$$

$$P \{ X=1 \} = e^{-2}\frac{2^1}{1!} \approx 0.2707$$

{: .highlight }

Một tính chất quan trọng khác là có thể **xấp xỉ phân phối nhị thức bằng phân phối Poisson** khi số lần thử lớn và xác suất thành công nhỏ, với tham số $$\lambda = np$$. Theo kinh nghiệm, khi phép thử nhị thức có **$$n \ge 100$$ và $$np \le 10$$** thì phân phối Poisson có thể cung cấp xấp xỉ tốt.

Ví dụ: Giả sử rằng 1% số ốc vít được sản xuất bởi một máy là lỗi. Tính xác suất rằng một lô 500 ốc vít có đúng 3 ốc vít lỗi.

- Sử dụng phân phối nhị thức: $$P \{ X = 3 \} = \binom{500}{3} (0.01)^3 (0.99)^{497}$$

Không giải được với máy tính cầm tay[^2]. Sử dụng thư viện scipy trên Python có thể tính xác suất.

```python
from scipy.stats import binom

#calculate binomial probability
binom.pmf(k=3, n=500, p=0.01)
```
```
0.1402
```

- Sử dụng phân phối Poisson: 

$$\lambda = np = 500 \cdot 0.01 = 5$$

$$P \{ X = 3 \} \approx e^{-5} \frac{5^3}{3!}$$

Máy tính cầm tay cho ra kết quả xấp xỉ 0.1404.

# Hypergeometric random variable

Phân phối xác suất siêu bội được dùng để tính xác suất như sau:

Cho một bộ bài có 20 lá gồm 6 đỏ và 14 đen. Chọn ngẫu nhiên 5 lá không hoàn lại bộ bài. Tình xác suất có 4 lá bài đỏ.

**Phân phối xác suất siêu bội khá gần với nhị thức**. Điểm khác nhau là:

{: .highlight }

- Các phép thử không độc lập.
- Xác suất thành công thay đổi từ phép thử này sang phép thử khác.

Gọi X là biến ngẫu nhiên cần quan tâm. **Hàm khối xác suất (PMF)** được trình bày như sau:

{: .highlight }

$$
P\{ X = x \} = f(x) = \frac{\binom{r}{x} \binom{N - r}{n - x}}{\binom{N}{n}}
$$

*Trong đó:

*$$x$$ = số lần thành công trong $$n$$ phép thử*

*$$N$$ = kích thước tổng thể*

*$$r$$ = số phần tử của tổng thể được xem là thành công*

Quay trở lại ví dụ 20 lá bài ở trên. Chúng ta xác định $$x = 4$$, $$n = 5$$, $$N = 20$$ và $$r = 6$$. 

$$P\{ X = 4 \} = \frac{\binom{6}{4} \binom{14}{1}}{\binom{20}{5}} = 0.0135$$

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

Eberly College of Science. (n.d.). 7.4 - Hypergeometric Distribution \| STAT 414. PennState: Statistics Online Courses. https://online.stat.psu.edu/stat414/lesson/7/7.4

Eberly College of Science. (n.d.). 11.4 - Negative Binomial Distributions \| STAT 414. PennState: Statistics Online Courses. https://online.stat.psu.edu/stat414/lesson/11/11.4

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

The Department of Mathematics and Computer Science. (n.d.). The connection between the poisson and binomial distributions. Emory Oxford College. https://math.oxford.emory.edu/site/math117/connectingPoissonAndBinomial/


# Notes
[^1]: Giá trị của hàm giữ nguyên hoặc tăng khi x tăng.
[^2]: Tác giả sử dụng Casio fx-580VN X.
