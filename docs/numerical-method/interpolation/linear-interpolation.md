---
layout: default
math: mathjax
title: Linear Interpolation
parent: Interpolation
grand_parent: Numerical Methods
nav_order: 1
---

# Linear Interpolation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


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

Giả sử cần tìm $$f(x)$$ khi $$x = 2$$, phương pháp đơn giản nhất là dùng nội suy tuyến tính đa thức bậc 1. Nội suy tuyến tính đa thức bậc 1 **nối hai điểm dữ liệu bất kì để tạo thành một đường thẳng** và chứa giá trị cần tìm trong đoạn đó. Công thức được trình bày như sau:

{: .highlight }

$$
f_1(x) = f(x_0) + \frac{f(x_1) - f(x_0)}{x_1 - x_0}(x - x_0)
$$

*Trong đó, $$f_1(x)$$ biểu thị cho nội suy tuyến tính đa thức bậc 1.*


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

# References

Anton, H. (2010). Elementary linear algebra. John Wiley & Sons.

Chapra, S. C., & Canale, R. P. (2016). Numerical methods for engineers.

Dao Nguyen, Anh (n.d.). Lecture: Interpolation. Numerical Methods. University of Economics HCMC.

Eusebius D. (n.d.). Lecture: Elementary Numerical Methods. Concordia University.

GeoGebra (2024). Dynamic Mathematics Software. https://www.geogebra.org.