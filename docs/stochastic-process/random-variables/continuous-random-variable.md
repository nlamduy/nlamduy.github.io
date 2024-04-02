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

1. Xác suất của biến ngẫu nhiên liên tục X nằm giữa đoạn $$(a,b)$$ là tích phân của hàm $$f_X$$ trên đoạn đó: $$P\{a \le X \le b\} = \int_a^b f_X(x)dx$$, cho $$a \le b$$

2. Xác suất của biến ngẫu nhiên liên tục X tại một điểm cụ thể gần như bằng 0: $$P\{X = a\} = \int_a^a f_X(x)dx = 0$$

3. Xác suất từ âm đến dương vô cực là 1: $$\int_{-\infty}^{+\infty} f_X(x)dx = 1$$

4. CDF của X là tích phân của hàm PDF trên đoạn $$(-\infty, x)$$: $$F_X(x) = \int_{-\infty}^x f_X(x)dx$$

5. PDF của X là đạo hàm CDF: $$\frac{dF(x)}{dx} = f(x)$$

Ở tính chất số (2), vì X có thể nhận vô hạn giá trị trên một đoạn (ví dụ từ 0 đến 1), nên xác suất tại một điểm gần như bằng 0.

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

Phân phối mũ là một phân phối quan trọng được sử dụng trong nhiều mô hình kinh tế, tài chính hoặc bảo hiểm. Phân phối mũ có tham số $$\lambda > 0$$ và hàm mật độ xác suất (PDF) được cho bởi:

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

Phân phối chuẩn (normal distribution) cũng là một trong những **phân phối quan trọng** và được ứng dụng rộng rãi. Cho X là biến ngẫu nhiên chuẩn **có hai tham số với trung bình (hay kỳ vọng) $$\mu > 0$$ và phương sai $$\sigma^2 > 0$$** (ký hiệu: $$X \sim N(0,1)$$), hàm mật độ xác suất (PDF) được cho bởi:

{: .highlight }

$$
f(x) = \frac{1}{\sqrt{2\pi}\sigma} e^{-(x - \mu)^2 / 2\sigma^2} \text{ , } -\infty < x < \infty
$$

![norm_eg1](/assets/img/stochastic-process/normal_eg1.png)

Ví dụ 1: 

Từ $$X \sim N(0,1)$$, có thể định nghĩa một biến $$Y = \alpha X + \beta$$ tuỳ ý, với $$Y \sim N(\beta, \alpha^2)$$. Cần lưu ý hai điểm sau:

{: .highlight }
- Cộng một hằng số $$\beta$$ vào biến ngẫu nhiên chuẩn chỉ làm thay đổi kỳ vọng (trung bình) của biến đó.
- Nhân một hệ số $$\alpha$$ vào biến ngẫu nhiên chuẩn sẽ làm thay đổi phương sai thành $$\alpha^2$$.

Trường hợp **trung bình $$\mu = 0$$ và độ lệch chuẩn $$\sigma = 1$$, ta có phân phối chuẩn chuẩn hoá** (standard normal distribution). **Ký tự $$z$$ thường được sử dụng** để ký hiệu cho biến ngẫu nhiên có phân phối đặc biệt này.

Công thức để chuyển đổi một biến ngẫu nhiên $$x$$ bất kỳ về phân phối chuẩn chuẩn hoá:

{: .highlight }

$$
z = \frac{x - \mu}{\sigma}
$$

Chuyển đổi về phân phối chuẩn chuẩn hoá sẽ giúp việc tính toán xác suất dễ dàng hơn, đặc biệt trong việc tính CDF. Việc chuyển đổi còn giúp chúng ta so sánh những biến có thang đo và phân phối khác nhau. Chẳng hạn, làm sao để so sánh điểm tiếng anh IELTS và TOEFL của hai sinh viên.

Sau khi tính được giá trị $$z$$, có thể sử dụng bảng xác suất chuẩn hoá[^1] để tìm xác suất mong muốn. Các phần mềm như Geogebra cũng cung cấp công cụ để giải và trực quan hoá các kết quả.

Ví dụ 1: Một cổ phiếu có lợi nhuận kỳ vọng là 5%, độ lệch chuẩn là 20% và tuân theo phân phối chuẩn. Tìm xác suất lợi nhuận từ 7%.

Tìm giá trị $$z$$:

$$
z = \frac{0.07 - 0.05}{0.2} = 0.1
$$

Sử dụng z table, có thể tra được xác suất $$P\{x < 0.07\} =0.5398$$. Như vậy, xác suất có lợi nhuận từ 7% là 46.02%.  

# References

Anderson, D. R., Sweeney, D. J., Williams, T. A., Camm, J. D., & Cochran, J. J. (2016). Statistics for Business & Economics. Cengage Learning.

CrashCourse. (2018, May 30). Z-Scores and Percentiles: Crash Course Statistics #18. [Youtube Video](https://www.youtube.com/watch?v=uAxyI_XfqXk).

Nguyen Huu, Thai (n.d.). Lecture: Random Variables. Stochastic models and applications. University of Economics HCMC.

Ross, S. M. (2019). Introduction to probability models. Academic Press.

# Notes

[^1]: Sử dụng https://www.z-table.com hoặc tương đương.