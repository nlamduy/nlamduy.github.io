---
layout: default
math: mathjax
title: Poisson Process
parent: Stochastic Process
nav_order: 5
---

# Poisson Process
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Counting process

Một quá trình ngẫu nhiên $$\{N(t), t \ge 0\}$$ được gọi là một **quá trình đếm** nếu $$N(t)$$ đại diện cho tổng số [biến cố](https://nlamduy.github.io/docs/stochastic-process/probability-theory/sample-space-events.html#events) xảy ra trong thời gian $$t$$.

Ví dụ: 

Xem xét quá trình [Bernoulli](https://nlamduy.github.io/docs/stochastic-process/random-variables/discrete-random-variable.html#bernoulli-and-binomial-random-variable) sau:

Tung một đồng xu trong 8 ngày và biến cố thành công là mặt ngửa (1). Giả sử kết quả tung đồng xu mỗi ngày là 00101011. Quá trình đếm $$N(t)$$ được mô tả bằng 00112234.

{: .note-title }
> Một số tính chất của quá trình đếm
>
> Cho một quá trình đếm $$\{ N(t), t \ge 0 \}$$ thoả mãn:
>
> 1. $$N(t) > 0 \text{, với mọi } t \ge 0$$
> 2. $$N(t) \text{ nhận giá trị nguyên (integer values)}$$
> 3. Nếu $$s < t$$ thì $$N(s) < N(t)$$
> 4. Cho $$s < t, N(t) - N(s)$$ bằng số lượng biến cố xảy ra trong nửa khoảng $$(s, t]$$

