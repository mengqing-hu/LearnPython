# Python array（数组）

Python 本身没有像 C/Java 那样的固定数组，常见的是：

- list（列表） → 最常用，功能最强大。
- array 模块 → 标准库里提供的 array.array，只能存放相同类型的数据，更像传统意义上的数组。
- NumPy 数组（ndarray） → 科学计算和数据分析最常用的数组。

#### 区别

| 特性       | **list（列表）**    | **array 模块（array.array）** | **NumPy 数组（ndarray）**    |
| -------- | --------------- | ------------------------- | ------------------------ |
| **数据类型** | 可以存放任意类型（甚至混合）  | 只能存放相同类型（用 typecode 指定）   | 只能存放相同类型（数值/布尔/字符串等）     |
| **存储方式** | 存储对象的引用，灵活但占内存大 | 连续内存，更接近 C 语言数组           | 高效的 C 实现，连续内存，专为科学计算优化   |
| **功能**   | 增删改查，通用容器       | 基础数组功能，类似 C/Java 数组       | 数学运算、矩阵操作、广播机制、线性代数、统计分析 |
| **性能**   | 适合通用编程，运算慢      | 比 list 更快，但功能少            | 性能最高，支持大规模数值计算           |
| **依赖**   | 内置              | 内置                        | 需要安装 NumPy 库             |
| **适用场景** | 一般数据存储、可混合类型    | 简单、低级的定长数值数组              | 科学计算、机器学习、图像处理、大数据运算     |

#### 常用功能对比

| 功能类别   | **list（列表）**                                   | **array.array**                                | **NumPy ndarray**                                                                       |
| ------ | ---------------------------------------------- | ---------------------------------------------- | --------------------------------------------------------------------------------------- |
| **创建** | `[1,2,3]`, `list()`                            | `array('i', [1,2,3])`                          | `np.array([1,2,3])`, `np.arange()`, `np.zeros()`                                        |
| **增**  | `append(x)`, `insert(i,x)`, `extend(iterable)` | `append(x)`, `extend(iterable)`, `insert(i,x)` | `np.append(arr,x)`, `np.concatenate()`, `np.vstack()`                                   |
| **删**  | `pop([i])`, `remove(x)`, `clear()`             | `pop([i])`, `remove(x)`                        | `np.delete(arr, i)`                                                                     |
| **改**  | `lst[i] = v`, `lst[start:end]=[...]`           | `arr[i] = v`（同类型限制）                            | `arr[i] = v`, 切片修改                                                                      |
| **查找** | `index(x)`, `count(x)`, `in`                   | `index(x)`, `count(x)`                         | `np.where(arr==x)`, `in` (`x in arr`)                                                   |
| **排序** | `sort()`, `sorted()`                           | ❌ 不支持                                          | `np.sort()`, `np.argsort()`                                                             |
| **反转** | `reverse()`, `lst[::-1]`                       | ❌ 不支持                                          | `np.flip(arr)`                                                                          |
| **统计** | `len()`, `max()`, `min()`, `sum()`             | `len()`, `max()`, `min()`, `sum()`             | `arr.shape`, `arr.ndim`, `arr.size`, `arr.dtype`, `arr.mean()`, `arr.std()`, `np.sum()` |
| **切片** | `lst[start:end:step]`                          | `arr[start:end:step]`                          | `arr[start:end:step, ...]`（支持多维）                                                        |
| **遍历** | `for x in lst`, `enumerate(lst)`               | `for x in arr`                                 | `for x in arr`, `np.nditer()`                                                           |
| **拷贝** | `copy()`, `list(a)`, `copy.deepcopy(a)`        | `arr.tolist()`（转成 list）                        | `arr.copy()`, `np.copy(arr)`                                                            |
| **特殊** | 可存混合类型                                         | 节省内存，必须同类型                                     | 支持广播、矩阵运算、线性代数、傅里叶变换等                                                                   |

### Numpy

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


