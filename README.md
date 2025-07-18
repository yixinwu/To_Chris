# To_Chris

Project 1: 
安装系统:    本次实验在Linux虚拟机上搭建，主要环境如下，其他需要的第三方
库及对应版本见requirements.txt。
（1）Linux: Ubuntu 20.04.6
（2）Python: 3.8
（3）JDK: 1.8
（4）Hadoop: 3.3.5
（5）Spark: 3.2.0
（6）运行软件：VS Code


[cite_start]好的，现在我有了论文的完整内容。文中第八页的 **Example 1** 位于 **3.3 节“编程线性变换”（Program computing linear transformations）** 的开始部分。然而，在提供的PDF文本中，**并没有明确标示为“Example 1”的独立例子**。这一节是直接从关于线性变换的定义和限制条件开始的 [cite: 172]。

看起来，用户可能将对线性指令的描述或对高斯消元法（Gaussian elimination）的引用误认为是“Example 1”。这一节的主要内容是**为线性变换的无内存计算设定理论框架**，而不是提供一个具体的计算实例。

我将详细解释这一节的内容，其中可能包括用户所指的“例子”的上下文：

[cite_start]**3.3节：编程线性变换 (Program computing linear transformations)** [cite: 172]

这一节关注的是在无内存计算框架下，如何处理特定类型的函数——**线性变换**。它的讨论建立在以下几个关键假设和概念之上：

1.  [cite_start]**有限域上的输入和字母表** [cite: 172]：
    * 本节假设计算是在一个**有限域** `A = GF(q)` 上进行的，其中 `q` 是一个素数的幂（例如，`GF(2)` 代表只有0和1的二进制域）。
    * 这意味着所有输入变量 `x1, ..., xn` 都是这个有限域中的元素。
    * 在有限域中，可以进行加法、乘法等算术运算，并且这些运算都满足域的性质（例如，每个非零元素都有乘法逆元）。

2.  [cite_start]**计算目标：线性变换** [cite: 172]：
    * 要计算的函数 `f` 是 `A^n` 上的一个**线性变换**。
    * 这意味着 `f(x)` 可以用矩阵乘法的形式表示为 `xM^T`，其中 `M` 是一个 `n x n` 的矩阵，且矩阵 `M` 的所有元素都来自有限域 `A`。
    * 函数 `f` 的每个坐标函数 `fi` 可以被看作是矩阵 `M` 的第 `i` 行向量与输入向量 `x` 的内积，即 `fi(x) = fi ⋅ x`。论文中提到这是一种“符号滥用”，但有助于理解。

3.  [cite_start]**指令限制：仅限线性指令** [cite: 173]：
    * 与论文前面章节讨论任意（可能非线性）指令不同，本节**严格限制只能使用线性指令**。
    * 线性指令的形式为 `yi ← a ⋅ y = Σj=1^n aj yj`，其中 `a = (a1, ..., an)` 是一个来自 `A^n` 的向量。这意味着每个寄存器的更新值都是当前所有寄存器值的线性组合。

4.  [cite_start]**矩阵计算的等价性** [cite: 174, 175, 176]：
    * 计算线性变换 `f(x) = xM^T` 等价于将矩阵 `M` 表示为一系列矩阵的乘积：`M = M1 ... ML`。
    * 这里的 `Mi` 是一个**只修改一行**的特殊矩阵。这意味着每一步操作（指令）只影响输出矩阵 `M` 的一行。
    * 如果 `M` 是非奇异矩阵（可逆矩阵），那么这个过程也等价于一系列非奇异矩阵 `N0=In, N1, ..., NL-1, NL=M` 的序列，其中 `Ni` 和 `Ni+1` 之间只相差一行。

5.  [cite_start]**与高斯消元法的联系** [cite: 177, 178]：
    * [cite_start]文章指出，“**高斯消元法（Gaussian elimination）表明，任何矩阵都可以通过只涉及两行的线性指令来计算**” [cite: 177]。
    * 这暗示了可以通过一系列基本行操作（对应于线性指令）来逐步构建或转换矩阵，从而实现任意线性变换的计算。高斯消元法本身就是通过一系列行操作将矩阵转化为行阶梯形或简化行阶梯形的方法，这些行操作包括行交换、行乘以非零常数、一行加上另一行的倍数，而这些操作都可以被视为只修改一行或两行的线性指令。

**总结**：

[cite_start]文中第八页的 3.3 节没有提供一个具体的“Example 1”来演示线性变换的无内存计算过程。相反，它**设定了在有限域上编程线性变换的理论基础和约束**。它强调了使用线性指令的条件，并将线性变换的计算问题等价于矩阵的分解问题，并提及了高斯消元法与这种计算方式的联系，暗示了实现路径 [cite: 172, 173, 174, 175, 176, 177, 178]。这部分内容为后续更深入的理论分析和复杂性度量奠定了基础。



Project 2: database获取和处理

