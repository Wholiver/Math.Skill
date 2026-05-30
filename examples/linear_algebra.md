# 矩阵的特征值与对角化

## 用户输入
求矩阵 $A = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix}$ 的特征值、特征向量，并求可逆矩阵 $P$ 和对角矩阵 $D$ 使得 $A = PDP^{-1}$。

## Skill 分类
线性代数

## 题意解析
- **已知条件**：$2 \times 2$ 实对称矩阵 $A = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix}$。
- **求解目标**：(1) 特征值 $\lambda_1, \lambda_2$；(2) 对应的特征向量 $\mathbf{v}_1, \mathbf{v}_2$；(3) 对角化 $A = PDP^{-1}$。
- **关键性质**：$A$ 是实对称矩阵，因此特征值均为实数，特征向量正交，且一定可对角化。
- **隐含条件**：$P$ 的列就是特征向量，$D$ 的对角线是特征值（顺序与 $P$ 中的特征向量对应）。

## 方法选择
**首选方法**：求解特征方程 $\det(A - \lambda I) = 0$ 得到特征值，再对每个 $\lambda$ 解齐次方程组 $(A - \lambda I)\mathbf{v} = \mathbf{0}$ 得到特征向量。

**备选方法**：利用对称矩阵的谱定理进行正交对角化。对于 $2 \times 2$ 矩阵，也可以直接用迹和行列式求特征值（$\lambda_1 + \lambda_2 = \text{tr}(A) = 6$，$\lambda_1 \lambda_2 = \det(A) = 8$）。

## 解题过程

### 第一步：求特征值

特征多项式：

$$\det(A - \lambda I) = \begin{vmatrix} 3 - \lambda & 1 \\ 1 & 3 - \lambda \end{vmatrix}$$

$$= (3 - \lambda)^2 - 1 = \lambda^2 - 6\lambda + 8 = (\lambda - 4)(\lambda - 2)$$

$$(\lambda - 4)(\lambda - 2) = 0$$

特征值：

$$\lambda_1 = 2,\quad \lambda_2 = 4$$

### 第二步：求特征向量

**对 $\lambda_1 = 2$**，解 $(A - 2I)\mathbf{v} = \mathbf{0}$：

$$\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$

即 $x + y = 0$，取 $x = 1$ 则 $y = -1$。

$$\mathbf{v}_1 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}$$

**对 $\lambda_2 = 4$**，解 $(A - 4I)\mathbf{v} = \mathbf{0}$：

$$\begin{pmatrix} -1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$$

即 $-x + y = 0$，取 $x = 1$ 则 $y = 1$。

$$\mathbf{v}_2 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}$$

### 第三步：构造 $P$ 和 $D$

$$P = \begin{pmatrix} \mathbf{v}_1 & \mathbf{v}_2 \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix}$$

$$D = \begin{pmatrix} \lambda_1 & 0 \\ 0 & \lambda_2 \end{pmatrix} = \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix}$$

### 第四步：验证 $A = PDP^{-1}$

求 $P^{-1}$：

$$\det(P) = 1 \cdot 1 - 1 \cdot (-1) = 2$$

$$P^{-1} = \frac{1}{2} \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}$$

验证：

$$PDP^{-1} = \frac{1}{2} \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix} \begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}$$

$$= \frac{1}{2} \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix} \begin{pmatrix} 2 & -2 \\ 4 & 4 \end{pmatrix} = \frac{1}{2} \begin{pmatrix} 6 & 2 \\ 2 & 6 \end{pmatrix} = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} = A$$

✓

## 验算

### 方法一：验证 $A\mathbf{v}_i = \lambda_i \mathbf{v}_i$

$$A\mathbf{v}_1 = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ -1 \end{pmatrix} = \begin{pmatrix} 3 - 1 \\ 1 - 3 \end{pmatrix} = \begin{pmatrix} 2 \\ -2 \end{pmatrix} = 2 \begin{pmatrix} 1 \\ -1 \end{pmatrix} = \lambda_1 \mathbf{v}_1$$

$$A\mathbf{v}_2 = \begin{pmatrix} 3 & 1 \\ 1 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \begin{pmatrix} 3 + 1 \\ 1 + 3 \end{pmatrix} = \begin{pmatrix} 4 \\ 4 \end{pmatrix} = 4 \begin{pmatrix} 1 \\ 1 \end{pmatrix} = \lambda_2 \mathbf{v}_2$$

✓

### 方法二：迹与行列式验证

$$\text{tr}(A) = 3 + 3 = 6 = 2 + 4 = \lambda_1 + \lambda_2$$

$$\det(A) = 3 \cdot 3 - 1 \cdot 1 = 8 = 2 \cdot 4 = \lambda_1 \lambda_2$$

✓

### 方法三：特征向量的正交性

$$\mathbf{v}_1 \cdot \mathbf{v}_2 = 1 \cdot 1 + (-1) \cdot 1 = 0$$

特征向量正交，符合实对称矩阵的性质。✓

## 最终答案

$$\boxed{\lambda_1 = 2,\; \mathbf{v}_1 = \begin{pmatrix} 1 \\ -1 \end{pmatrix}}$$

$$\boxed{\lambda_2 = 4,\; \mathbf{v}_2 = \begin{pmatrix} 1 \\ 1 \end{pmatrix}}$$

$$\boxed{P = \begin{pmatrix} 1 & 1 \\ -1 & 1 \end{pmatrix},\quad D = \begin{pmatrix} 2 & 0 \\ 0 & 4 \end{pmatrix},\quad A = PDP^{-1}}$$

## 易错点
1. **特征方程的符号**：$\det(A - \lambda I) = 0$ 还是 $\det(\lambda I - A) = 0$？前者展开后特征多项式为 $(-1)^n \det(\lambda I - A)$，两者对求特征值等价，但注意符号细节。
2. **特征向量的顺序**：$P$ 中特征向量的顺序必须与 $D$ 对角线上特征值的顺序一致。若交换 $\mathbf{v}_1$ 和 $\mathbf{v}_2$ 的位置，$D$ 的对角线也应变为 $\operatorname{diag}(4, 2)$。
3. **特征向量缩放**：特征向量不唯一（可乘以任意非零标量），但 $PDP^{-1}$ 的结果不变。
4. **检查可对角化前提**：不是所有矩阵都可对角化（如 Jordan 块）。实对称矩阵天然可对角化，但一般矩阵需要检查几何重数 = 代数重数。
