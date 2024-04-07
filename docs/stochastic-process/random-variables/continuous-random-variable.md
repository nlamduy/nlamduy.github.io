---
layout: default
math: mathjax
title: Continuous Random Variables
parent: Random Variables
grand_parent: Stochastic Process
nav_order: 2
---

# Continuous Random Variables
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

{: .highlight }

$$
P\{X \in B\} = \int_B f_X(x)dx
$$

*Trong đó: $$B \subset \mathbb{R}$$*


Ví dụ:

Tính xác suất $$P\{X > 3\}$$ với $$B = (3, +\infty)$$: 

$$P\{X > 3\} = \int_3^{+\infty} f_X(x)dx$$

**Một số tính chất cơ bản:**

{: .highlight }

1. Xác suất của biến ngẫu nhiên liên tục X nằm giữa khoảng $$(a; b)$$ là tích phân của hàm $$f_X$$ trên đoạn đó: $$P\{a \le X \le b\} = \int_a^b f_X(x)dx$$, cho $$a \le b$$

2. Xác suất của biến ngẫu nhiên liên tục X tại một điểm cụ thể gần như bằng 0: $$P\{X = a\} = \int_a^a f_X(x)dx = 0$$

3. Xác suất từ âm đến dương vô cực là 1: $$\int_{-\infty}^{+\infty} f_X(x)dx = 1$$

4. CDF của X là tích phân của hàm PDF trên khoảng $$(-\infty; x)$$: $$F_X(x) = \int_{-\infty}^x f_X(x)dx$$

5. PDF của X là đạo hàm CDF: $$\frac{dF(x)}{dx} = f(x)$$

Ở tính chất số (2), vì X có thể nhận vô hạn giá trị trên một khoảng (ví dụ từ 0 đến 1), nên xác suất tại một điểm gần như bằng 0.

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

![pdf_eg1](/assets/img/stochastic-process/pdf_eg1.png)

# Uniform random variable

Phân phối đều được sử dụng nếu **xác suất trong khoảng bất kỳ cũng bằng với xác suất trong khoảng khác**. Hàm mật độ xác suất (PDF) được cho bởi:

{: .highlight }

$$
f(x) = \begin{cases} 
\frac{1}{\beta - \alpha}  & \text{ , if } \alpha < x < \beta \\
0 & \text{ , otherwise}
\end{cases}
$$

Phân phối đều thường được dùng để diễn tả những sự kiện đơn giản, hoặc cho mục đích giả lập (simulation).

Giả sử thời gian di chuyển từ nhà đến công ty có thể nhận bất kỳ giá trị nào trong khoảng từ 30 đến 45 phút. Xác suất di chuyển trong khoảng 35 đến 40 phút là bao nhiêu?

$$
P\{35 < X < 40\} = (40-35) \cdot \frac{1}{45-30} = \frac{5}{15} = \frac{1}{3} \approx 0.33
$$

Vậy xác suất di chuyển trong khoảng từ 35 đến 40 phút là $$\frac{1}{3}$$ hoặc khoảng 33.33%.

Trực quan hoá với Python:

![uni_eg1](/assets/img/stochastic-process/uni_eg1.png)

Như vậy, xác suất là diện tích của hình chữ nhật với chiều cao là $$\frac{1}{45 - 30}$$ và chiều rộng là $$P\{35 < X < 40\}$$.

# Exponential random variable

Phân phối mũ có tham số $$\lambda > 0$$ và hàm mật độ xác suất (PDF) được cho bởi:

{: .highlight }

$$
f(x) = \begin{cases} 
\lambda e^{-\lambda x}  & \text{ , if } x > 0 \\
0 & \text{ , otherwise}
\end{cases}
$$


Một số ứng dụng của phân phối mũ như tính xác suất giữa các lượt khách hàng đến quầy giao dịch, khoảng cách giữa các ổ gà trên đường.


Ví dụ: thời gian trung bình để xử lý một hồ sơ vay là 15 phút và tuân theo phân phối mũ. Tìm xác suất hồ sơ được xử lý trong 6 đến 18 phút.

$$\lambda = \frac{1}{\mu} = \frac{1}{15}$$


Hàm PDF: $$f(x) = \lambda e^{-\lambda x}$$

Hàm CDF: $$F_X(x) = 1 - e^{-\lambda x}$$

$$P\{6 < X < 18\} = \int_6^{18} \lambda e^{-\lambda x}dx$$


$$P\{6 < X < 18\} = (1 - e^{-\frac{1}{15} \cdot 18}) - (1 - e^{-\frac{1}{15} \cdot 6}) = 0.3691$$

Trực quan hoá với Python:

![exp_eg1](/assets/img/stochastic-process/exp_eg1.png)

{: .highlight }

Tương tự như phân phối hình học (geometric distribution), phân phối mũ cũng có **tính không nhớ**.

$$
P\{X > x + t | X > t\} = P\{X > s\}
$$

Giả sử, một khách hàng đã chờ 15 phút ở ngân hàng, xác suất phải chờ thêm 5 phút để được phục vụ không bị ảnh hưởng bởi quá khứ.

Mối quan hệ giữa phân phối Poisson và phân phối mũ có thể được diễn đạt như sau: Phân phối Poisson dùng để tính xác suất số lần xuất hiện trong một khoảng không gian, thời gian. Phân phối mũ cung cấp xác suất của khoảng giữa các lần xuất hiện.

# Normal random variable

## Normal distribution

Cho X là biến ngẫu nhiên chuẩn **có hai tham số với trung bình (hay kỳ vọng) $$\mu > 0$$ và phương sai $$\sigma^2 > 0$$** (ký hiệu: $$X \sim N(0,1)$$), hàm mật độ xác suất (PDF) được cho bởi:

{: .highlight }

$$
f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-(x - \mu)^2 / 2\sigma^2} \text{ , } -\infty < x < \infty
$$

![norm_eg1](/assets/img/stochastic-process/normal_eg1.png)

Từ $$X \sim N(0,1)$$, có thể định nghĩa một biến $$Y = \alpha X + \beta$$ tuỳ ý, với $$Y \sim N(\beta, \alpha^2)$$. Cần lưu ý hai điểm sau:

{: .highlight }
- Cộng một hằng số $$\beta$$ vào biến ngẫu nhiên chuẩn chỉ làm thay đổi kỳ vọng (trung bình) của biến đó.
- Nhân một hệ số $$\alpha$$ vào biến ngẫu nhiên chuẩn sẽ làm thay đổi phương sai thành $$\alpha^2$$.

**Một số đặc điểm của phân phối chuẩn:**

{: .highlight }
1. Các phân phối chuẩn được phân biệt bởi 2 tham số: trung bình $$\mu$$ và độ lệch chuẩn $$\sigma$$ (hoặc phương sai $$\sigma^2$$).
2. Điểm cao nhất của đường cong chuẩn nằm tại vị trí trung bình, đây cũng là trung vị (median) và mode của phân phối.
3. Giá trị trung bình của phân phối chuẩn có nhận bất kỳ số nào (âm, dương, bằng 0).
4. Phân phối chuẩn là đối xứng với hai đuôi kéo dài đến vô cực.
5. Độ lệch chuẩn quy định độ rộng và phẳng (kurtosis) của đường cong chuẩn.
6. Xác suất được cho bởi diện tích nằm dưới đường cong chuẩn.
7. Phần trăm để giá trị của biến ngẫu nhiên nằm trong khoảng thông dụng[^2] là:
- 68.3% giá trị sẽ nằm trong khoảng $$(\mu - \sigma; \mu + \sigma)$$
- 95.4% giá trị sẽ nằm trong khoảng $$(\mu - 2\sigma; \mu + 2\sigma)$$
- 99.7% giá trị sẽ nằm trong khoảng $$(\mu - 3\sigma; \mu + 3\sigma)$$



## Standard normal distribution

Trường hợp **trung bình $$\mu = 0$$ và độ lệch chuẩn $$\sigma = 1$$, ta có phân phối chuẩn chuẩn hoá** (standard normal distribution). **Ký tự $$z$$ thường được sử dụng** để ký hiệu cho biến ngẫu nhiên có phân phối đặc biệt này.

Công thức để chuyển đổi một biến ngẫu nhiên $$x$$ bất kỳ về phân phối chuẩn chuẩn hoá:

{: .highlight }

$$
z = \frac{x - \mu}{\sigma}
$$

Chuyển đổi về phân phối chuẩn chuẩn hoá sẽ giúp việc tính toán xác suất dễ dàng hơn, đặc biệt trong việc tính CDF. Việc chuyển đổi còn giúp chúng ta so sánh những biến có thang đo và phân phối khác nhau. Chẳng hạn, làm sao để so sánh điểm tiếng anh IELTS và TOEFL của hai sinh viên.

Sau khi tính được giá trị $$z$$, có thể sử dụng bảng xác suất chuẩn hoá[^1] để tìm xác suất mong muốn. Các phần mềm như Geogebra cũng cung cấp công cụ để giải và trực quan hoá các kết quả.

Ví dụ 1: 

Một cổ phiếu có lợi nhuận kỳ vọng là 5%, độ lệch chuẩn là 20% và tuân theo phân phối chuẩn. Tìm xác suất lợi nhuận từ 7%.

Tìm giá trị $$z$$:

$$
z = \frac{0.07 - 0.05}{0.2} = 0.1
$$

Sử dụng z table, có thể tra được xác suất $$P\{x < 0.07\} =0.5398$$. Như vậy, xác suất có lợi nhuận từ 7% là 46.02%.  

Ví dụ 2: Vấn đề của Công ty Lốp xe Grear

Trung bình số dặm lốp xe chịu được là $$\mu = 36,500$$km, với độ lệch chuẩn $$\sigma = 5000$$, và tuân theo phân phối chuẩn.

a. Tìm xác suất lốp xe chịu được $$x > 40,000$$km. 

b. Công ty Grear sẽ giảm giá khi thay lốp nếu xe bị hỏng trong số dặm bảo hành. Tuy nhiên, Grear không muốn có hơn 10% số lốp xe đủ điều kiện bảo hành. Tìm số dặm bảo hành đảm bảo điều kiện này.

Trả lời:

a. Tìm giá trị $$z = \frac{40000 - 36500}{5000} = 0.7$$

```python
import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt

probability = 1 - stats.norm.cdf(0.7)

print(f"The probability that the tire lasts more than 40,000km is {probability}")
```
```
The probability that the tire lasts more than 40,000km is 0.24196365222307303
```

b. Dùng z-table có thể xác định $$z = -1.28$$ tương ứng với phần diện tích 10% ở đuôi trái phân phối chuẩn. Suy ra, $$x = 30100$$ km sẽ thoả điều kiện chỉ khoảng 10% lốp xe đủ điều kiện bảo hành.

Có thể sử dụng Python như bên dưới:

```python
# Find the mileage
mileage = stats.norm.ppf(0.1, loc=36500, scale=5000)

print(f"The mileage for the warranty to ensure no more than 10% of tires are eligible is {mileage} km")

```
```
The mileage for the warranty to ensure no more than 10% of tires are eligible is 30092.242172276998 km
```
![normal_eg2](/assets/img/stochastic-process/normal_eg2.png)

## Normal approximation of binomial probabilities

Khi số lượng phép thử của biến nhị thức lớn, cụ thể $$np \ge 5$$ và $$n(1 - p) \ge 5$$, với $$n$$ là số lượng phép thử và $$p$$ là xác suất thành công. Có thể sử dụng phân phối chuẩn để xấp xỉ nhị thức với $$\mu = np$$ và $$\sigma = \sqrt{np(1-p}$$.

Lấy lại ví dụ ở phần xấp xỉ phân phối nhị thức với phân phối Poisson. Giả sử rằng 1% số ốc vít được sản xuất bởi một máy là lỗi. Tính xác suất rằng một lô 500 ốc vít có đúng 3 ốc vít lỗi.

- Kết quả từ phân phối nhị thức với Python:

```python
from scipy.stats import binom

#calculate binomial probability
binom.pmf(k=3, n=500, p=0.01)
```
```
0.1402
```

- Kết quả từ xấp xỉ Poisson:

$$\lambda = np = 500 \cdot 0.01 = 5$$

$$P \{ X = 3 \} \approx e^{-5} \frac{5^3}{3!} \approx 0.1404$$


- Kết quả từ xấp xỉ phân phối chuẩn:

$$\mu = np = 500 * 0.01 = 5$$

$$\sigma = \sqrt{np(1-p)} = \sqrt{500 * 0.01 * 0.99} \approx 2.23$$

Vì phân phối chuẩn là liên tục, ta không thể tìm trực tiếp $$x = 3$$ mà phải sử dụng **yếu tố điều chỉnh tính liên tục (continuity correction)** để tìm xác suất có 3 ốc vít lỗi trong lô 500 ốc vít. Do đó, cần tìm $$z$$ với $$x = 2.5$$ và $$x = 3.5$$ như sau:

```python
# Calculate the Z-scores
Z_2_5 = (2.5 - 5) / 2.23
Z_3_5 = (3.5 - 5) / 2.23

# Calculate the probabilities
probability_2_5 = stats.norm.cdf(Z_2_5)
probability_3_5 = stats.norm.cdf(Z_3_5)

# Find the probability for exactly 3 defective screws
probability_3 = probability_3_5 - probability_2_5

print(f"The probability that a batch of 500 screws has exactly 3 defective screws is {probability_3}")
```
```
The probability that a batch of 500 screws has exactly 3 defective screws is 0.1194586403509098
```

![normal_eg3](/assets/img/stochastic-process/normal_eg3.png)

**Từ các kết quả trên, xấp xỉ phân phối nhị thức của phân phối Poisson cho giá trị gần giá trị thực tế hơn phân phối chuẩn.**

# Gamma random variable

Phân phối gamma là một dạng **tổng quát hoá của phân phối mũ**. Phân phối mũ, phân phối chi-square là những trường hợp đặc biệt của phân phối gamma. Một trong những ứng dụng điển hình của phân phối gamma là **tính xác suất thời gian chờ giữa các sự kiện**, với tốc độ trung bình $$\lambda$$ không đổi.

Cho biến ngẫu nhiên X tuân theo phân phối Gamma với $$\alpha > 0$$ và $$\lambda > 0$$, hàm mật độ xác suất (PDF) được cho bởi:

{: .highlight }

$$
f(x) = \begin{cases}
\frac{\lambda e^{-\lambda x}(\lambda x)^{\alpha - 1}}{\Gamma(\alpha)} \text{ , if } x \ge 0 \\
0 \text{ , otherwise }
\end{cases}
$$

Trong đó:

- Nếu $$\alpha$$ thuộc tập số thực ($$\alpha \in \mathbb{R}$$), hàm gamma được định nghĩa [^3]:

$$
\Gamma(\alpha) = \int_0^{\infty} e^{-x} x^{\alpha - 1} dx
$$


- Nếu $$\alpha$$ thuộc tập nguyên dương ($$\alpha \in \mathbb{Z}^+$$):

$$
\Gamma(\alpha) = (\alpha - 1)!
$$

Ví dụ 1:

Các kỹ sư thiết kế thế hệ tàu vũ trụ tiếp theo dự định sẽ bao gồm hai bơm nhiên liệu — một bơm đang hoạt động, bơm còn lại dự phòng. Nếu bơm chính gặp sự cố, bơm thứ hai sẽ tự động được đưa vào hoạt động. Giả sử một nhiệm vụ điển hình dự kiến sẽ cần bơm nhiên liệu tối đa 50 giờ. Theo thông số kỹ thuật của nhà sản xuất, bơm dự kiến sẽ hỏng một lần mỗi 100 giờ. Khả năng hệ thống bơm nhiên liệu như vậy không hoạt động liên tục trong suốt 50 giờ là bao nhiêu?

Ta có: $$\lambda = \frac{1}{100}$$, $$\alpha = 2$$.

Hàm PDF:

$$
f_X(x) = \frac{\frac{1}{100} \cdot e^{- \frac{1}{100} \cdot x}(\frac{1}{100} \cdot x)^{2 - 1}}{(2-1)!}
$$

Hàm CDF:

$$
P\{X < 50\} = \int_0^{50} f_X(x) dx \approx 0.0902
$$

Sử dụng Python:

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import gamma

# Parameters of the Gamma distribution
k = 2
theta = 100

# Calculate the CDF at 50 hours
x = 50
cdf_at_x = gamma.cdf(x, k, scale=theta)

# Calculate the probability that the system does fail within 50 hours
prob_fail = cdf_at_x

print(f"The probability that the system does fail within 50 hours is {prob_fail}")
```
```
The probability that the system does fail within 50 hours is 0.09020401043104986
```

![gamma_eg1](/assets/img/stochastic-process/gamma_eg1.png)

Ví dụ 2: 

Trung bình cứ mỗi 2 phút sẽ có 1 người đi thang máy vào giờ cao điểm. Cho X là biến ngẫu nhiên đại diện cho thời gian chờ và tuân theo phân phối gamma. Tính xác suất chờ từ 5 đến 10 phút đến khi người thứ 5 đến.

Ta có: $$\lambda = \frac{1}{\beta} = \frac{1}{2}$$, $$\alpha = 5$$.

Tìm $$P\{5 < X < 10\}$$ với công cụ tính xác suất từ [GeoGebra](https://www.geogebra.org/calculator):

![gamma_eg2](/assets/img/stochastic-process/gamma_eg2.png)

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

CrashCourse. (2018, May 30). Z-Scores and Percentiles: Crash Course Statistics #18. [Youtube Video](https://www.youtube.com/watch?v=uAxyI_XfqXk).

Eberly College of Science. (n.d.). 15.7 - A gamma example \| STAT 414. PennState: Statistics Online Courses. https://online.stat.psu.edu/stat414/lesson/15/15.7

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

# Appendix

## Exponential random variable

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import expon

# Parameters
mean = 15  # average time to process a loan application
lambda_ = 1 / mean  # rate parameter for the exponential distribution

# Calculate the probability
prob = expon.cdf(18, scale=mean) - expon.cdf(6, scale=mean)

print(f"The probability that the loan application will be processed in 6 to 18 minutes is {prob:.4f}")

# Visualization
x = np.linspace(0, 30, 1000)
y = expon.pdf(x, scale=mean)

plt.figure(figsize=(8, 6))
plt.plot(x, y, label="Exponential distribution")
plt.fill_between(x, y, where=(6 <= x) & (x <= 18), color="red", alpha=0.3, label="6 to 18 minutes")
plt.title("Exponential Distribution of Loan Processing Time")
plt.xlabel("Time (minutes)")
plt.ylabel("Probability Density Function (pdf)")
plt.legend()
plt.grid(True)
plt.show()

```

## Normal random variable

```python
import matplotlib.pyplot as plt
import numpy as np
from scipy.stats import norm

# Set the mean (mu) and standard deviations (sigma)
mu = 0
sigmas = [0.5, 1.0, 1.5]

# Create a range of x values
x = np.linspace(-5, 5, 100)

# Plot each normal distribution
for sigma in sigmas:
    plt.plot(x, norm.pdf(x, mu, sigma), label=f'sigma={sigma}')

# Add title and legend, then show the plot
plt.title('Normal Distributions with Same Mean and Different Variances')
plt.legend()
plt.show()
```

```python
# Generate data
x = np.linspace(20000, 50000, 1000)
y = stats.norm.pdf(x, 36500, 5000)

# Create the plot
plt.figure(figsize=(10,6))
plt.plot(x, y)

# Shade the area under the curve for part a
x_fill_a = np.linspace(40000, 50000, 1000)
y_fill_a = stats.norm.pdf(x_fill_a, 36500, 5000)
plt.fill_between(x_fill_a, y_fill_a, alpha=0.5, color='blue', label='P(X > 40000)')

# Shade the area under the curve for part b
x_fill_b = np.linspace(20000, mileage, 1000)
y_fill_b = stats.norm.pdf(x_fill_b, 36500, 5000)
plt.fill_between(x_fill_b, y_fill_b, alpha=0.5, color='orange', label='Eligible 10%')

# Show the plot
plt.title('Normal Distribution of Tire Durability')
plt.xlabel('Mileage (km)')
plt.ylabel('Probability Density')
plt.legend()
plt.show()
```

```python
# Calculate the Z-scores
Z_2_5 = (2.5 - 5) / 2.23
Z_3_5 = (3.5 - 5) / 2.23

# Calculate the probabilities
probability_2_5 = stats.norm.cdf(Z_2_5)
probability_3_5 = stats.norm.cdf(Z_3_5)

# Find the probability for exactly 3 defective screws
probability_3 = probability_3_5 - probability_2_5

# Generate data
x = np.linspace(0, 10, 1000)
y = stats.norm.pdf(x, 5, 2.23)

# Create the plot
plt.figure(figsize=(10,6))
plt.plot(x, y)

# Shade the area under the curve for exactly 3 defective screws
x_fill = np.linspace(2.5, 3.5, 1000)
y_fill = stats.norm.pdf(x_fill, 5, 2.23)
plt.fill_between(x_fill, y_fill, alpha=0.5, color='red', label='P(X = 3)')

# Show the plot
plt.title('Normal Distribution of Defective Screws')
plt.xlabel('Number of Defective Screws')
plt.ylabel('Probability Density')
plt.legend()
plt.show()

print(f"The probability that a batch of 500 screws has exactly 3 defective screws is {probability_3}")

```

## Gamma random variable

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import gamma

# Parameters of the Gamma distribution
k = 2
theta = 100

# Calculate the CDF at 50 hours
x = 50
cdf_at_x = gamma.cdf(x, k, scale=theta)

# Calculate the probability that the system does fail within 50 hours
prob_fail = cdf_at_x

print(f"The probability that the system does fail within 50 hours is {prob_fail}")

# Plot the Gamma distribution
x = np.linspace(0, 200, 1000)
y = gamma.pdf(x, k, scale=theta)

plt.figure(figsize=(12, 6))
plt.plot(x, y, label='Gamma distribution')
plt.fill_between(x, y, where=(x<=50), color='red', alpha=0.5, label='Area under curve within 50 hours')
plt.title('Gamma Distribution of Fuel Pump Failures')
plt.xlabel('Time (hours)')
plt.ylabel('Probability Density Function (PDF)')
plt.legend()
plt.grid(True)
plt.show()

```

# Notes

[^1]: Sử dụng https://www.z-table.com hoặc tương đương.

[^2]: Xem thêm quy tắc thực nghiệm (Emperical rule).

[^3]: Xem thêm tích phân suy rộng.