---
layout: default
math: mathjax
title: Newton Interpolating Polynomials
parent: Interpolation
grand_parent: Numerical Methods
nav_order: 1
---

# Newton Interpolating Polynomials
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

Nội suy đa thức Newton là một trong những phương pháp phổ biến và hữu dụng vì có thể tăng bậc của đa thức để đạt được sai số ước lượng nhỏ như mong muốn. Nội suy đa thức Newton là nền tảng cho nhiều phương pháp nội suy khác. Hai dạng đơn giản nhất của nội suy đa thức Newton là nội suy bậc một (tuyến tính) và nội suy bậc hai.

# First-order interpolating polynomial

Cho tập dữ liệu bên dưới:

| x  | f(x)   |
|----|--------|
| 1  | 0      |
| 3  | 1.0986 |
| 4  | 1.3863 |
| 5  | 1.6094 |
| 6  | 1.7918 |

Trong nhiều trường hợp, chúng ta không xác định được hàm số $$f(x)$$, _như trong trường hợp này $$f(x) = \ln(x)$$_, mà chỉ có giá trị của $$f(x)$$ cho bởi $$x$$. 

Giả sử cần tìm $$f(x)$$ khi $$x = 2$$, phương pháp đơn giản nhất là dùng **nội suy tuyến tính**. Nội suy tuyến tính **nối hai điểm dữ liệu bất kì để tạo thành một đường thẳng** và chứa giá trị cần tìm trong đoạn đó. Công thức được trình bày như sau:

{: .highlight }

$$
f_1(x) = f(x_0) + \frac{f(x_1) - f(x_0)}{x_1 - x_0}(x - x_0)
$$

*Trong đó, $$f_1(x)$$ biểu thị cho nội suy đa thức bậc 1.*


Ví dụ: Tìm giá trị $$f(x)$$ khi $$x = 2$$, biết $$f(1) = 0$$, $$f(3) = 1.0986$$ và $$f(4) = 1.3863$$ (giá trị thực tế $$f(2) = 0.6931$$).

Sử dụng nội suy tuyến tính: 

- Trường hợp 1:  $$f(1) = 0$$, $$f(4) = 1.3863$$

$$f_1(2) = f(1) + \frac{f(4) - f(1)}{4 - 1}(2 - 1) = 0 + \frac{1.386 - 0}{3} \cdot 1  = 0.462$$

- Trường hợp 2: $$f(1) = 0$$, $$f(3) = 1.0986$$

$$f_1(2) = 0.5493$$

![lin_interp1_eg1](/assets/img/numerical-methods/lin_interp1_eg1.png)

Quan sát đồ thị trên ta thấy, khi thu hẹp đoạn chứa $$x = 2$$ ($$d(x_1, x_4) \to d(x_1, x_3)$$) thì giá trị ước tính được ($$A(2, 0.462) \to B(2, 0.5493)$$) càng gần với thực tế ($$\text{actual}(2, 0.6931)$$).

Lập trình với Python:

```python
import numpy as np

# Hàm nội suy tuyến tính đa thức bậc 1
def lin_interp1(x, fx, point):

    # Tìm giá trị nhỏ hơn và lớn hơn gần nhất với giá trị x cần tìm

    s_idx = None
    g_inx = None
    
    for i, num in enumerate(x):
        if num < point:
            if s_idx is None or num > fx[s_idx]:
                s_idx = i
        elif num > point:
            if g_inx is None or num < fx[g_inx]:
                g_inx = i
    
    # Nội suy tuyến tính đa thực bậc 1

    f1 = fx[s_idx] + (fx[g_inx] - fx[s_idx]) / (x[g_inx] - x[s_idx]) * (point - x[s_idx])

    return print('Giá trị xấp xỉ tốt nhất là: ', f1)

x = np.array([1, 3, 4, 5, 6])
fx = np.array([0, 1.0986, 1.3863, 1.6094, 1.7918])

lin_interp1(x=x, fx=fx, point=2)
```
```
Giá trị xấp xỉ tốt nhất là:  0.5493
```

Sử dụng thư viện có sẵn:

```python
import timeit
import numpy as np
from scipy.interpolate import interp1d

start = timeit.default_timer()

X = np.array([1, 3, 4, 5, 6])
Y = np.array([0, 1.0986, 1.3863, 1.6094, 1.7918])

# test value
interpolate_x = 2

# Finding the interpolation
y_interp = interp1d(X, Y, kind='linear')
print("Value of Y at x = {} is".format(interpolate_x),
	y_interp(interpolate_x))

# Finding runtime performance
stop = timeit.default_timer() 

print('Time: ', stop - start)  
```
```
Value of Y at x = 2 is 0.5493
Time:  0.006623812999805523
```

# Quadratic interpolation

Phương pháp **nội suy tuyến tính thường tạo ra sai số lớn** do chúng ta đang sử dụng đường thẳng nối giữa hai điểm để ước tính giá trị của $$f(x)$$. **Nếu sử dụng ba điểm, sử dụng nội suy đa thức bậc 2 sẽ cho ước lượng tốt hơn**. Công thức được trình bày như sau:

{: .highlight }
$$
f_2(x) = b_0 + b_1(x - x_0) + b_2(x - x_0)(x - x_1)
$$

*Trong đó, $$f_2$$ biểu thị cho nội suy đa thức bậc 2*.

Các **hệ số hồi quy (hệ số góc)** được tính toán như bên dưới:

{: .highlight }

$$
b_0 = f(x_0)
$$

{: .highlight }

$$
b_1 = \frac{f(x_1) - f(x_0)}{x_1 - x_0}
$$

{: .highlight }

$$
b_2 = \frac{\frac{f(x_2) - f(x_1)}{x_2 - x_1} - \frac{f(x_1) - f(x_0)}{x_1 - x_0}}{x_2 - x_0}
$$

Ví dụ: Sử dụng bảng dữ liệu ở phần [First-order interpolating polynomial](#first-order-interpolating-polynomial), tìm $$f(2)$$ sử dụng phương pháp nội suy đa thức bậc 2.

- Chọn 3 điểm: $$x_0 = 1, x_1 = 3, x_2 = 4$$; $$f(x_0) = 0, f(x_1) = 1.0986, f(x_2) = 1.3863$$.

- Tìm hệ số hồi quy: $$b_0 = 0, b_1 = 0.5493, b_2 = -0.0872$$

- Tìm $$f_2(2)$$: $$f_2(2) = 0 + 0.5493(2 - 1) + (-0.0872)(2 - 1)(2 - 3) = 0.6365$$

Chúng ta biết giá trị chính xác của $$\ln(2) \approx 0.6931$$, với phương pháp nội suy tuyến tính $$f_1(2) = 0.5493$$, còn nội suy đa thức bậc 2 $$f_2(2) = 0.6365$$.

```python
import timeit
import numpy as np
from scipy.interpolate import interp1d

start = timeit.default_timer()

X = np.array([1, 3, 4, 5, 6])
Y = np.array([0, 1.0986, 1.3863, 1.6094, 1.7918])

# test value
interpolate_x = 2

# Finding the interpolation
y_interp = interp1d(X, Y, kind='quadratic')
print("Value of Y at x = {} is".format(interpolate_x),
	y_interp(interpolate_x))

# Finding runtime performance
stop = timeit.default_timer()

print('Time: ', stop - start)  
```
```
Value of Y at x = 2 is 0.6422198198198198
Time:  0.011491664000004675
```

# General form of Newton's interpolating polynomials

Từ công thức nội suy tuyến tính và nội suy đa thức bậc 2 ở trên, công thức tổng quát cho n-bậc đa thức hay nội suy đa thức Newton được trình bày:

{: .highlight }
$$
\begin{aligned}
f_n(x) = f(x_0) + f[x_1, x_0](x - x_0) + f[x_2, x_1, x_0](x - x_0)(x - x_1)\\
 + ... + f[x_n, x_{n-1}, ..., x_0](x - x_0)(x - x_1) ... (x - x_{n-1})
\end{aligned}
$$

Ví dụ: Sử dụng bảng dữ liệu ở phần [First-order interpolating polynomial](#first-order-interpolating-polynomial), tìm $$f(2)$$ sử dụng phương pháp nội suy đa thức bậc 3.

- Chọn 4 điểm: 

$$x_0 = 1, x_1 = 3, x_2 = 4, x_3 = 5$$

$$f(x_0) = 0, f(x_1) = 1.0986, f(x_2) = 1.3863, f(x_3) = 1.6094$$

- Tìm hệ số hồi quy $$b_3$$ (các hệ số $$b_0, b_1, b_2$$ đã được tính trước đó):

$$b_3 = \frac{\frac{\frac{f(x_3) - f(x_2)}{x_3 - x_2} - \frac{f(x_2) - f(x_1)}{x_2 - x_1}}{x_3 - x_1} - b_2}{x_3 - x_0} \approx 0.0057$$

- Tìm $$f(2)$$:

$$f(x_2) = f(x_0) + b_1(x - x_0) + b_2(x - x_0)(x - x_1) + b_3(x - x_0)(x - x_1)(x - x_2)$$

$$f(x_2) = 0.6475$$


```python
import timeit
import numpy as np
from scipy.interpolate import interp1d

start = timeit.default_timer()

X = np.array([1, 3, 4, 5, 6])
Y = np.array([0, 1.0986, 1.3863, 1.6094, 1.7918])

# test value
interpolate_x = 2

# Finding the interpolation
y_interp = interp1d(X, Y, kind='cubic')
print("Value of Y at x = {} is".format(interpolate_x),
	y_interp(interpolate_x))

# Finding runtime performance
stop = timeit.default_timer()

print('Time: ', stop - start)
```
```
Value of Y at x = 2 is 0.667388235294118
Time:  0.008166161000190186
```


# References

Anton, H. (2010). Elementary linear algebra. John Wiley & Sons.

Chapra, S. C., & Canale, R. P. (2016). Numerical methods for engineers. McGraw Hill.

Dao Nguyen, Anh (n.d.). Lecture: Interpolation. Numerical Methods. University of Economics HCMC.

Eusebius D. (n.d.). Lecture: Elementary Numerical Methods. Concordia University.

GeoGebra (2024). Dynamic Mathematics Software. https://www.geogebra.org.