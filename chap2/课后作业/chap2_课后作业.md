# 1. 分析为什么平方损失函数不适用于分类问题.

- 分类问题中的标签，是没有连续的概念的。每个标签之间的距离也是没有实际意义的，所以预测值 和 标签两个向量之间的平方差这个值不能反应分类这个问题的优化程度。 

- 假设分类问题的类别是1,2,3

- 那么对于一个真实类别为2的样本X，模型的分类结果是 1 或 3，平方损失函数得到的结果都一样。

- 显然，不适合

# 2. 计算其最优参数

在线性回归中，如果我们给每个样本 $\left(\mathbf{x}^{(n)}, y^{(n)}\right)$ 赋予一个权重 $r^{(n)}$，经验风险函数为
$$
\mathcal{R}(\mathbf{w})=\frac{1}{2} \sum_{n=1}^{N} r^{(n)}\left(y^{(n)}-\mathbf{w}^{\mathrm{T}} \mathbf{x}^{(n)}\right)^{2}
$$
计算其最优参数 $w^*​$，并分析权重 $r^{(n)}​$ 的作用。
$$
\begin{array}{l}
\frac{\partial R(w)}{\partial w}=-r x\left(y-x^{T} w\right)=0 \
\left. \\
w^{*}=(\sum_{n=1}^{N} x^{(n)}\left(x^{(n)}\right)^{T}\right)^{-1}\left(\sum_{n=1}^{N} r^{(n)} x^{(n)} y^{(n)}\right)
\end{array}
$$

# 3. 证明

在线性回归中，如果样本数量 N 小于特征数量 d+1，则 XX^T 的秩最大为 N。

答：
- 已知定理：设 $A, B$ 分别为 $n \times m, m \times s$的矩阵，则 $rank(AB) \le min\{rank(A), rank(B)\}$

- 而 $X \in \mathbb{R}^{(d+1) \times N}, X^T \in \mathbb{R}^{N \times (d+1)}​$

   - $rank(X) = rank(X^T) = min((d+1), N), N < d + 1, 可知 rank(X) = N$

- 可知 $rank(X, X^T) \le {N, N} = N​$

# 4. 验证岭回归

在线性回归中，验证岭回归的解为 结构风险最小化准则 下的最小二乘法估计，见公式(2.44)

答：
已知
$$
R(w) = \frac{1}{2}||y - X^Tw||^2 + \frac{1}{2}\lambda ||w||^2   \\
w^* = (XX^T + \lambda I)^{-1}Xy
$$

可得
$$
\begin{aligned}
\frac{\partial \mathcal{R}(\mathbf{w})}{\partial \mathbf{w}} &=\frac{1}{2} \frac{\partial\left\|\mathbf{y}-X^{\mathrm{T}} \mathbf{w}\right\|^{2}+\lambda\|\mathbf{w}\|^{2}}{\partial \mathbf{w}} \\
&=-X\left(\mathbf{y}-X^{\mathrm{T}} \mathbf{w}\right)+\lambda \mathbf{w}
\end{aligned}
$$

令 $\frac{\partial}{\partial \mathrm{w}} \mathcal{R}(\mathbf{w})=0$ 可得

$$
\begin{array}{c}
-X Y+X X^{\mathrm{T}} \mathbf{w}+\lambda \mathbf{w}=0 \\
\left(X X^{\mathrm{T}}+\lambda I\right) \mathbf{w}=X Y
\end{array}
$$

即
$$
\mathbf{w}^{*}=\left(X X^{\mathrm{T}}+\lambda I\right)^{-1} X \mathbf{y}
$$

$$
\begin{array}{c}
-X Y+X X^{\mathrm{T}} \mathbf{w}+\lambda \mathbf{w}=0 \\
\left(X X^{\mathrm{T}}+\lambda I\right) \mathbf{w}=X Y
\end{array}
$$

即

$$
\mathbf{w}^{*}=\left(X X^{\mathrm{T}}+\lambda I\right)^{-1} X \mathbf{y}
$$

# 5. 最大似然估计

在线性回归中，若假设标签 $y \sim \mathcal{N} \left(\mathbf{w}^{\mathrm{T}} \mathbf{x}, \beta\right)$ 并用最大似然估计来优化参数时，验证最优参数为公式(2.51)的解。

已知
$$
\log p(\mathbf{y} \mid X ; \mathbf{w}, \sigma)=\sum_{n=1}^{N} \log \mathcal{N}\left(y^{(n)} \mid \mathbf{w}^{\mathrm{T}} \mathbf{x}^{(n)}, \sigma^{2}\right)
$$
$\begin{aligned} \text { 令 } \frac{\partial \log p(\mathrm{y} \mid X ; \mathbf{w}, \sigma)}{\partial \mathrm{w}}=0, \text { 即有 } \\ & \frac{\partial\left(\sum_{n=1}^{N}-\frac{\left(y^{(n)}-\mathrm{w}^{\mathrm{T}} \mathbf{x}^{(n)}\right)^{2}}{2 \beta}\right)}{\partial \mathbf{w}}=0 \\ & \frac{\partial \frac{1}{2}\left\|\mathbf{y}-X^{\mathrm{T}} \mathbf{w}\right\|^{2}}{\partial \mathbf{w}}=0 \\ &-X\left(\mathbf{y}-X^{\mathrm{T}} \mathbf{w}\right)=0 \end{aligned}​$
$$
\begin{aligned} & \\ & \end{aligned}
$$










