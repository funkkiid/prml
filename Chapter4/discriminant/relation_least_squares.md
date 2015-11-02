确定线性判别式的最小二乘方法是基于使模型预测尽可能的接近目标值的目的的。相反，Fisher准则的目标是最大化输出空间中类别的区分度。这两种方法之间的关系是很有趣的。特别的，我们会证明，在二分类问题中，Fisher准则可以看成最小二乘的一个特例。    

目前为止，我们一直采用“1-of-K”编码来表示目标值。然而，如果我们采用一种稍微不同的编码方式，那么权重的最小二乘解会等价于Fisher判别式的解（Duda and Hart, 1973）。特别的，我们让属于$$ C_1 $$的目标值等于$$ N/N_1 $$，其中$$ N_1 $$是类别$$ C_1 $$的模式的数量，$$ N $$是总的模式数量。这个目标值近似于类别$$ C_1 $$的先验概率的倒数，同时令$$ C_2 $$目标值等于$$ −N/N_2 $$，其中$$ N_2
$$是类别$$ C_2 $$的模式的数量。    

平方和误差函数可以写成

$$
E = \frac{1}{2}\sum\limits_{n=1}^N\left(w^Tx_n + w_0 - t_n \right)^2 \tag{4.31}
$$

分别关于$$ w_0, w $$求$$ E $$的导数，并使其等于0，得到

$$
\begin{eqnarray}
\sum\limits_{n=1}^N\left(w^Tx_n + w_0 - t_n \right) = 0 \tag{4.32} \\
\sum\limits_{n=1}^N\left(w^Tx_n + w_0 - t_n \right)x_n = 0 \tag{4.33}
\end{eqnarray}
$$

根据式（4.32），并按选择的目标编码方式来编码$$ t_n $$，就可得到偏置的表示式

$$
w_0 = -w^Tm \tag{4.34}
$$

其中我们使用了

$$
\sum\limits_{n=1}^Nt_n = N_1\frac{N}{N_1} - N_2\frac{N}{N_2} = 0 \tag{4.35}
$$

且$$ m $$是由

$$
m = \frac{1}{N}\sum\limits_{n=1}^Nx_n = \frac{1}{N}(N_1m_1 + N_2m_2) \tag{4.36}
$$

给出的全部数据的均值。通过一些简单的代数计算，并再次使用$$ t_n $$的选定编码方式，第二个方程（4.33）就变成

$$
\left(S_W + \frac{N_1N_2}{N}S_B\right)w = N(m_1 - m_2) \tag{4.37}
$$

其中$$ S_W, S_B $$分别有式（4.28）（4.27）定义，并代入了式（4.34）的偏置定义。通过式（4.27）我们知道$$ S_Bw $$总是在$$ (m_2 - m_1) $$的方向上。因此得到

$$
w \propto S_W^{-1}(m_2 - m_1) \tag{4.38}
$$

其中我们忽略了不相关的标量因子。因此权向量恰好与由Fisher判别准则得到的结果相同。此外，我们也发现，式（4.34）给出偏置$$ w_0 $$的表达式。这告诉我们，对于一个新的向量$$ x $$，如果$$ y(x) = w^T(x − m) > 0 $$，那么它应该被分到$$ C_1 $$，否则就应该被分到$$ C_2 $$。
