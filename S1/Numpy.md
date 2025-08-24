1. NumPy（Numerical Python）是一个 开源科学计算库, 它的底层是 C/Fortran 写的，比 Python 自带的 list 快很多。

2. NumPy 的核心：ndarray

3. 广播机制是 NumPy 中的一种自动扩展数组形状以便进行运算的规则。当两个数组形状不同，但某些维度兼容时，NumPy 会自动“复制”小数组，使它们形状相同后再进行逐元素运算。广播不会真的复制数据，只是“虚拟扩展”，节省内存。如果维度不兼容，会报错。

4. ndarray 的浅拷贝和深拷贝的区别？
- 浅拷贝：切片产生的是视图（View），数据共享
- 深拷贝：copy() 会复制数据，互不影响

5. 什么是 NumPy？它与 Python list 有什么区别？
- NumPy 是 Python 的一个科学计算库，核心是高性能的多维数组对象 ndarray。
- 与 Python list 区别：
- - 存储方式：NumPy 使用连续内存，Python list 是对象数组。
- - 性能：NumPy 支持底层 C 实现的向量化运算，速度远快于Python list 循环。
- - 功能：NumPy 提供线性代数、傅里叶变换、统计分析等函数。

6. NumPy 与 pandas 的区别？什么时候用 NumPy？
- NumPy：侧重数值计算和矩阵运算
- Pandas：在 NumPy 基础上，提供 Series 和 DataFrame，适合结构化数据分析
- 用 NumPy 处理 矩阵运算、科学计算、ML 算法底层实现

7. NumPy 如何进行向量化运算？为什么比 Python loop 快？
- 直接用数组运算（如 a+b）而不是循环
- 底层用 C 实现，避免 Python 解释器开销，性能更高
