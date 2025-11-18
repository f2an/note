# SSE 量子蒙卡中磁化率的计算

线性响应函数，即磁化率的定义是：

$$\chi_{AB}=\frac {\partial \langle A(b)\rangle}{\partial b}$$

其中 $b$ 是附加的外场 $bB$ 的系数， $A$ 是需要计算的响应算符。

## 1. 理论计算
令 $H=H_0-bB$

Dyson 展开：

$$\exp(-\beta H)=\exp(-\beta H_0)[1+b\int_0^\beta d\tau e^{\tau H_0}Be^{-\tau H_0}]$$

所以：

$$Z=tr(e^{-\beta H})=tr[e^{-\beta H_0} (1+bB)]=Z_0+Z_0b\beta\langle B\rangle_0$$

$B$ 在 $H_0$ 下的期望值与时间无关。

$$\langle A(b)\rangle=tr[A(b)e^{-\beta H} ]\\ =\frac{Z_0\langle A\rangle_0+bZ_0\int_0^\beta\langle AB(\tau)\rangle d\tau}{Z_0(1+b\beta\langle B\rangle_0)}$$

泰勒展开到一阶：

$$\langle A(b)\rangle=\langle A\rangle_0+b\int_0^\beta\langle A(\tau)B(0)\rangle d\tau -b\beta\langle A\rangle\langle B\rangle$$

代入可得：

$$\chi_{AB}=\int_0^\beta\langle A(\tau)B(0)\rangle d\tau -\beta\langle A\rangle\langle B\rangle$$

## 2. SSE 蒙卡中的测量
$$\langle A \rangle=\frac 1Z tr(Ae^{-\beta (H-bB)})$$

$$\chi_{AB}=\frac{\partial}{\partial b} \frac 1Z tr(Ae^{-\beta (H-bB)})|_{b=0} \\ = \frac 1Z\frac{\partial}{\partial b} tr(Ae^{-\beta (H-bB)})|_{b=0} -\langle A\rangle \frac 1Z \frac{\partial Z}{\partial b} |_{b=0}$$

后一项 $\langle A\rangle $一般为零，现计算前一项：

$$ \chi_{AB} = \frac 1Z\frac{\partial}{\partial b} tr(Ae^{-\beta (H-bB)})|_{b=0} \\

=\frac 1Z \frac{\partial}{\partial b}\sum_\alpha\sum_{n=0}^\infty \frac{(-\beta)^n}{n!}\langle\alpha|A(H-bB)^n|\alpha\rangle |_{b=0} \\

=\frac 1Z \sum_\alpha\sum_{n=1}^\infty \sum_{m=0}^{n-1} \frac{-(-\beta)^n}{n!}\langle\alpha|AH^mBH^{n-m-1}|\alpha\rangle \\ =\frac 1Z \sum_\alpha\sum_{n=0}^\infty \sum_{m=0}^{n} \frac{\beta(-\beta)^n}{(n+1)!}\langle\alpha|AH^mBH^{n-m}|\alpha\rangle \\$$

### (1) 若 A 、 B 为对角算符，则
$$ \chi_{AB}=\frac 1Z \sum_\alpha\sum_{n=0}^\infty \frac{(-\beta)^n}{n!} \frac{\beta}{n+1}\sum_{p=0}^n A(0)B(p) \langle\alpha|H^n|\alpha\rangle \\=\langle\frac{\beta}{n+1}\sum_{p=0}^n A(0)B(p) \rangle =\langle\frac{\beta}{n(n+1)}\sum_{p=0}^n \sum_{m=0}^{n-1}A(m)B(m+p) \rangle\\=\langle\frac{\beta}{n(n+1)}\sum_{p=0}^{n-1} \sum_{m=0}^{n-1}A(m)B(m+p) \rangle+\langle\frac{\beta}{n(n+1)}\sum_{m=0}^{n-1}A(m)B(m) \rangle \\=\left\langle\frac{\beta}{n(n+1)} \left( \sum_{p=0}^{n-1}A(p) \sum_{p=0}^{n-1}B(p)+\sum_{p=0}^{n-1}A(p)B(p) \right)\right\rangle \\ $$

### (2) 若 A、B为非对角算法，且为哈密顿量里面的一部分，令 $H=\sum_m H_m$ 则

$$ \chi_{AB}=\frac 1Z \sum_\alpha\sum_{n=0}^\infty \sum_{m=0}^{n} \frac{\beta(-\beta)^n}{(n+1)!}\langle\alpha|AH^mBH^{n-m}|\alpha\rangle \\=\frac 1Z \sum_\alpha\sum_{n=0}^\infty \sum_{S_{n+2}} \sum_{m=0}^{n} \frac{\beta(-\beta)^n}{(n+1)!}\langle\alpha|AH_1\cdots H_mBH_{m+1}\cdots H_n|\alpha\rangle \\=\frac 1Z \sum_\alpha\sum_{n=0}^\infty \sum_{S_{n}} \sum_{m=0}^{n-2} \frac{(-\beta)^{n}}{(n)!} \frac {n}{\beta} \langle\alpha|AH_1\cdots H_mBH_{m+1}\cdots H_{n-2}|\alpha\rangle \\=\frac 1Z \sum_\alpha\sum_{n=0}^\infty \sum_{S_{n}} \sum_{m=0}^{n-2} \frac{-(-\beta)^{n-1}}{(n-1)!}\langle\alpha|AH_1\cdots H_mBH_{m+1}\cdots H_{n-2}|\alpha\rangle \\=\frac 1 \beta \langle \sum_{m=0}^{n-1} N(p_A-p_B=m)\rangle \\ $$
其中 $N(p_A-p_B=m)$ 指的是A和B的虚时距离为m的算符对数目，因此：

$$ \chi_{AB}=\frac 1\beta[\langle N(A)N(B)\rangle-\delta_{A,B}\langle N_A\rangle] $$