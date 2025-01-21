# 数据库

## 一.NumPy

`NumPy`是Python中用于科学计算的核心库，提供了高效的数组操作和数学运算功能。它的核心是`ndarray`对象，这是一种支持多维数组的数据结构，允许进行各种数学操作。

### 1. **`NumPy`数组：**`ndarray`

`ndarray`是`NumPy`的核心数据结构，它是一个多维数组对象，支持快速操作。

#### 创建`ndarray`

- 从列表或元组创建数组：

  ```python
  arr = np.array([1, 2, 3])
  print(arr)
  #[1 2 3]
  ```

- 创建零数组和单位数组：

  ```python
  zeros_arr = np.zeros((2, 3))  # 2行3列的零矩阵
  ones_arr = np.ones((3, 3))    # 3行3列的单位矩阵
  
  #[[0. 0. 0.]
  # [0. 0. 0.]]
  
  #[[1. 1. 1.]
  # [1. 1. 1.]
  # [1. 1. 1.]]
  ```

- 使用`arange`和`linspace`创建数组：

  ```python
  arr = np.arange(0, 10, 2)  # 创建从0到10（不包括10），步长为2的数组
  arr2 = np.linspace(0, 1, 5)  # 创建0到1之间的5个等间距点
  
  #[0 2 4 6 8]
  
  #[0.   0.25 0.5  0.75 1.  ]
  ```

#### 查看数组的属性：

```python
arr.shape  # 数组的形状
arr.size   # 数组的元素总数
arr.ndim   # 数组的维度
arr.dtype  # 数组的数据类型
```

```python
import numpy as np
arr = np.array([[1,2,3,4,5],[6,7,8,9,10]])
print(arr.shape)
print(arr.ndim)
print(arr.size)
print(arr.dtype)

#(2, 5) --2行5列
#2      --二维
#10     --10个数
#int64  --64位的整数类型
```



### 2. **数组操作**

#### 索引与切片

- 基本索引：

  ```python
  arr[0]    # 访问第一个元素
  arr[1:3]  # 切片，获取第1到第2个元素
  ```

- 多维数组索引：

  ```python
  arr = np.array([[1, 2, 3], [4, 5, 6]])
  arr[0, 1]  # 获取第一行第二列的元素
  ```

#### 改变数组形状：

```python
arr = np.array([1, 2, 3, 4, 5, 6])
reshaped_arr = arr.reshape((2, 3))  # 将一维数组变为2行3列

#[[1 2 3]
# [4 5 6]]
```

#### 数组连接与拆分：

- 连接数组：

  ```python
  arr1 = np.array([1, 2])
  arr2 = np.array([3, 4])
  np.concatenate((arr1, arr2))  # 将两个数组拼接,注意有2个括号
  print(np.contatennate((arr1,arr2)))
  ```

- 拆分数组：

  ```python
  np.split(arr, 2)  # 将数组分成两部分,其中size为偶数
  ```

  ```python
  import numpy as np
  arr = np.array([1,2,3,4,5,6])
  print(np.split(arr,2))
  
  #[array([1, 2, 3]), array([4, 5, 6])]
  ```



### 3. **数组运算**

- **按元素运算**：NumPy允许按元素进行加法、减法、乘法、除法等操作。

  ```python
  arr1 = np.array([1, 2, 3])
  arr2 = np.array([4, 5, 6])
  arr3 = arr1 + arr2  # 按元素相加
  print(arr3)
  
  #[5 7 9]
  ```

- **广播机制**：NumPy支持“广播”，即允许不同形状的数组进行运算，只要它们的维度兼容。

  ```python
  arr1 = np.array([1, 2, 3])
  arr2 = np.array([10])
  arr3 = arr1 + arr2  # 广播机制，使arr2扩展为[10, 10, 10]与arr1相加
  
  #[11,12,13]
  ```

- **通用函数（ufunc）**：NumPy提供了大量的数学函数，操作数组时会自动向量化处理（即逐元素运算）。

  ```python
  np.sin(arr)  # 计算数组元素的正弦值
  np.log(arr)  # 计算数组元素的自然对数
  ```

### 4. **常用数学函数**

- **线性代数**：

  ```python
  np.dot(a, b)      # 点积
  np.cross(a, b)    # 叉积
  np.linalg.inv(a)  # 求矩阵的逆
  np.linalg.det(a)  # 求矩阵的行列式
  ```

- **统计函数**：

  ```python
  np.mean(arr)      # 计算均值
  np.median(arr)    # 计算中位数
  np.std(arr)       # 计算标准差
  np.var(arr)       # 计算方差
  ```

### 5. **随机数生成**

NumPy提供了随机模块`numpy.random`，用于生成随机数。

```python
np.random.rand(3, 3)  # 创建3x3的均匀分布随机数组
np.random.randn(3, 3) # 创建3x3的标准正态分布随机数组
np.random.randint(0, 10, size=(3, 3))  # 生成3x3的随机整数数组，范围是0-10
```

### 6. **文件I/O操作**

- **保存数组到文件**：

  ```python
  np.save('array.npy', arr)  # 保存为二进制文件
  np.savetxt('array.txt', arr)  # 保存为文本文件
  ```

- **从文件加载数组**：

  ```python
  arr = np.load('array.npy')  # 从二进制文件加载
  arr = np.loadtxt('array.txt')  # 从文本文件加载
  ```

### 7. **高级特性**

- **结构化数组**：允许定义具有字段名称的数组。

  ```python
  dtype = np.dtype([('name', 'S10'), ('age', 'i4')])
  arr = np.array([('Alice', 25), ('Bob', 30)], dtype=dtype)
  ```

- **掩码数组**：可以使用布尔数组来掩盖不需要的值，类似于缺失数据的处理。

  ```python
  arr = np.array([1, 2, 3, 4, 5])
  mask = arr > 3
  masked_arr = np.ma.masked_array(arr, mask=mask)
  ```



## 二.matplotlib

`Matplotlib` 是一个强大的 Python 绘图库，用于生成各种类型的图表，广泛应用于数据分析、科学计算以及机器学习中。它能够生成高质量的静态、动态和交互式图表，支持丰富的自定义功能。

### 1. **导入 `Matplotlib`**

通常导入 `matplotlib.pyplot` 模块，简写为 `plt`：

```python
import matplotlib.pyplot as plt
```

### 2. **基础绘图**

#### (1)**折线图（Line Plot）**

折线图是最常见的图表类型，用于展示数据随时间或某个变量的变化。

```python
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y)
plt.title('Line Plot')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.show()
```

#### (2) **散点图（Scatter Plot）**

散点图展示了数据点之间的关系，常用于查看两个变量之间的相关性。

```python
x = np.random.rand(50)
y = np.random.rand(50)

plt.scatter(x, y)
plt.title('Scatter Plot')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.show()
```

#### (3) **柱状图（Bar Chart）**

柱状图展示分类数据的频率或数值。

```python
categories = ['A', 'B', 'C', 'D']
values = [10, 20, 15, 30]

plt.bar(categories, values)
plt.title('Bar Chart')
plt.xlabel('Categories')
plt.ylabel('Values')
plt.show()
```

#### (4) **直方图（Histogram）**

直方图用于显示数据的分布情况。

```python
data = np.random.randn(1000)

plt.hist(data, bins=30, edgecolor='black')
plt.title('Histogram')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.show()
```

#### (5) **饼图（Pie Chart）**

饼图通常用于展示分类数据的百分比。

```python
sizes = [25, 30, 45]
labels = ['A', 'B', 'C']

plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.title('Pie Chart')
plt.show()
```

### 4. **多图展示（Subplots）**

可以在一个图形窗口中展示多个图。

```python
fig, axs = plt.subplots(2, 2)  # 2x2的子图
axs[0, 0].plot(x, y)            # 第一张子图
axs[0, 1].scatter(x, y)         # 第二张子图
axs[1, 0].bar(categories, values) # 第三张子图
axs[1, 1].hist(data, bins=30)   # 第四张子图

plt.tight_layout()  # 自动调整子图间距
plt.show()
```

### 5. **图表自定义**

#### (1) **标题和标签**

```python
plt.plot(x, y)
plt.title('My Plot Title', fontsize=16)
plt.xlabel('X-axis Label', fontsize=12)
plt.ylabel('Y-axis Label', fontsize=12)
plt.show()
```

#### (2) **设置图例**

图例用于标记不同的数据系列或线条。

```python
plt.plot(x, y, label='sin(x)')
plt.plot(x, np.cos(x), label='cos(x)')
plt.legend(loc='upper right')
plt.show()
```

#### (3) **设置网格**

```python
plt.plot(x, y)
plt.grid(True)  # 显示网格
plt.show()
```

#### (4) **线条样式和颜色**

```python
plt.plot(x, y, linestyle='--', color='r', linewidth=2)  # 红色虚线
plt.show()
```

#### (5) **设置坐标轴范围**

```python
plt.plot(x, y)
plt.xlim(0, 10)  # 设置x轴的显示范围
plt.ylim(-1, 1)  # 设置y轴的显示范围
plt.show()
```

#### (6) **调整刻度**

```python
plt.plot(x, y)
plt.xticks(np.arange(0, 11, 1))  # x轴显示刻度
plt.yticks(np.arange(-1, 1.1, 0.2))  # y轴显示刻度
plt.show()
```

### 6. **图形保存**

将绘制的图形保存为图片文件（如 `PNG, PDF, SVG`等）。

```python
plt.plot(x, y)
plt.title('Save Plot Example')
plt.savefig('plot.png')  # 保存为PNG文件
```

### 7. **高级图形类型**

#### (1) **等高线图（Contour Plot）**

等高线图通常用于表示三维数据的二维投影。

```python
x = np.linspace(-5, 5, 100)
y = np.linspace(-5, 5, 100)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

plt.contour(X, Y, Z)
plt.title('Contour Plot')
plt.show()
```

#### (2) **三维图形（3D Plot）**

`matplotlib` 支持三维图形，通过 `Axes3D` 模块进行绘制。

```python
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

x = np.linspace(-5, 5, 100)
y = np.linspace(-5, 5, 100)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

ax.plot_surface(X, Y, Z, cmap='viridis')
plt.show()
```

#### (3) **热图（Heatmap）**

热图用于显示二维数据矩阵的颜色强度。

```python
data = np.random.rand(10, 10)
plt.imshow(data, cmap='hot', interpolation='nearest')
plt.colorbar()  # 显示颜色条
plt.show()
```

#### (4) **箱型图（Boxplot）**

箱型图显示数据的分布情况，特别适用于查看异常值。

```python
data = np.random.randn(100)
plt.boxplot(data)
plt.title('Boxplot')
plt.show()
```

### 8. **动画**

`matplotlib` 也支持创建动态图表，可以用 `FuncAnimation` 来生成动画。

```python
from matplotlib.animation import FuncAnimation

fig, ax = plt.subplots()
x = np.linspace(0, 2 * np.pi, 100)
y = np.sin(x)
line, = ax.plot(x, y)

def update(frame):
    line.set_ydata(np.sin(x + frame / 10))
    return line,

ani = FuncAnimation(fig, update, frames=100, interval=50)
plt.show()
```

### 9. **交互式图表**

通过 `matplotlib` 与 `IPython` 或 `Jupyter Notebook` 配合使用，可以创建交互式图表。

```python
%matplotlib notebook
plt.plot(x, y)
plt.show()
```

### 10. **自定义颜色**

- 使用 `cmap` 参数设置颜色映射。
- `viridis`, `plasma`, `inferno`, `magma` 等是常用的颜色图谱。

```python
plt.scatter(x, y, c=y, cmap='viridis')
plt.colorbar()  # 添加颜色条
plt.show()
```

### 11. **样式和主题**

`Matplotlib` 允许通过 `plt.style.use()` 选择不同的图表样式。

```python
plt.style.use('ggplot')  # 使用类似ggplot的风格
plt.plot(x, y)
plt.show()
```

### 12. **多种图形的组合**

可以在同一个图中同时绘制多种图形类型。

```python
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y, label='Sine Wave')
plt.scatter(x, y, color='r', label='Scatter Points')
plt.legend()
plt.show()
```



## 三,pandas库

### 1. **Pandas 数据结构**

- **Series**：一维标签化数组，类似于列表，可以存储任意数据类型。每个元素都可以有一个标签（即索引）。

```python
import pandas as pd

# 创建 Series
s = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
print(s)

#a    1
#b    2
#c    3
#d    4
#dtype: int64
```

- **DataFrame**：二维表格结构，包含行和列，每一列是一个 Series。它是 pandas 最常用的数据结构。

```python
# 创建 DataFrame
data = {'A': [1, 2, 3], 'B': [4, 5, 6]}
df = pd.DataFrame(data)
print(df)

#   A  B
#0  1  4
#1  2  5
#2  3  6
```

### 2. **数据导入与导出**

Pandas 支持多种文件格式的数据输入和输出，常见的包括` CSV、Excel、JSON、SQL`等。

```python
# 从 CSV 文件读取
df = pd.read_csv('data.csv')

# 从 Excel 文件读取
df = pd.read_excel('data.xlsx', sheet_name='Sheet1')

# 将 DataFrame 输出到 CSV 文件
df.to_csv('output.csv', index=False)

# 将 DataFrame 输出到 Excel 文件
df.to_excel('output.xlsx', index=False)
```

还可以指定其他参数（如编码、分隔符等）来定制读取或写入的行为：

```python
# 读取 CSV 文件时指定分隔符
df = pd.read_csv('data.txt', sep='\t')
```

### 3. **数据选择和索引**

**索引与切片**： Pandas 允许通过标签或位置来访问数据，支持多种索引方式。

- **使用** `**.loc[]**` **和** `**.iloc[]**` **进行选择**：
  - `.loc[]`: 按标签选择（包括起始和结束标签）
  - `.iloc[]`: 按位置选择（基于 0 的整数索引）

```python
# 按标签选择一行
df.loc[0]

# 按位置选择一行
df.iloc[0]

# 选择特定的列
df['A']

# 按行列选择
df.loc[0, 'A']  # 选择第 0 行的 'A' 列
df.iloc[0, 0]   # 选择第 0 行第 0 列
```

**多重索引**： Pandas 还支持多重索引（Hierarchical Indexing），可以使用多层级的行和列索引，适用于复杂的数据结构。

```python
# 创建多重索引
index = pd.MultiIndex.from_tuples([('A', 1), ('A', 2), ('B', 1)], names=['Letter', 'Number'])
df = pd.DataFrame({'Value': [10, 20, 30]}, index=index)
print(df)
```

### 4. **数据清理与处理**

- **缺失值处理**：
  - `isna()`：检测缺失值
  - `fillna()`：填充缺失值
  - `dropna()`：删除含有缺失值的行或列

```python
# 检查缺失值
df.isna()

# 填充缺失值
df.fillna(0, inplace=True)

# 删除含有缺失值的行
df.dropna(inplace=True)
```

- **重复数据**：
  - `drop_duplicates()`：删除重复数据
  - `duplicated()`：标记重复行

```python
# 删除重复行
df.drop_duplicates(inplace=True)

# 标记重复行
df.duplicated()
```

- **数据类型转换**：
  - `astype()`：转换数据类型

```python
# 转换列的数据类型
df['column_name'] = df['column_name'].astype(int)
```

### 5. **数据操作与转换**

- **排序**：
  - `sort_values()`：按值排序
  - `sort_index()`：按索引排序

```python
# 按列排序
df.sort_values(by='column_name', ascending=False, inplace=True)

# 按索引排序
df.sort_index(inplace=True)
```

- **字符串操作**：使用 `str` 属性对字符串列进行操作，如替换、分割、大小写转换等。

```python
# 字符串列转换为大写
df['column_name'] = df['column_name'].str.upper()

# 字符串列替换
df['column_name'] = df['column_name'].str.replace('old', 'new')
```

- **应用函数**：
  - `apply()`：将函数应用于列或行
  - `map()`：将函数应用于单列

```python
# 对每个元素应用一个函数
df['column_name'] = df['column_name'].apply(lambda x: x * 2)
```

- **条件筛选**： 通过布尔索引筛选数据。

```python
# 筛选出值大于 50 的行
df[df['column_name'] > 50]
```

### 6. **数据聚合与分组**

- **GroupBy 操作**：按列分组并应用聚合函数。

```python
# 按 'Category' 列分组，并计算每组的平均值
grouped = df.groupby('Category')
grouped.mean()

# 对每个组应用多个聚合函数
grouped.agg({'column1': 'sum', 'column2': 'mean'})
```

- **透视表**：`pivot_table()` 用于创建类似 Excel 的透视表。

```python
# 创建透视表
df.pivot_table(values='Value', index='Category', columns='SubCategory', aggfunc='mean')
```

### 7. **时间序列分析**

Pandas 提供了丰富的时间序列功能，支持日期时间索引、日期范围生成、重采样等操作。

- **日期范围生成**： 使用 `date_range()` 生成指定范围的日期。

```python
dates = pd.date_range('2023-01-01', periods=5, freq='D')
```

- **时间重采样**： 使用 `resample()` 进行时间序列的重采样。

```python
# 按月重采样并计算平均值
df.resample('M').mean()
```

- **日期时间转换**： 将字符串列转换为日期时间类型。

```python
df['date_column'] = pd.to_datetime(df['date_column'])
```

- **时间偏移**： 使用 `shift()` 实现数据的时间偏移。

```python
df['shifted'] = df['value_column'].shift(1)  # 将数据向下平移一行
```

### 8. **合并与连接数据**

- **合并**： 使用 `merge()` 函数来按列进行 SQL 风格的连接操作（内连接、外连接、左连接、右连接）。

```python
df1 = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df2 = pd.DataFrame({'A': [3, 4, 5], 'C': [7, 8, 9]})

# 合并两个 DataFrame
pd.merge(df1, df2, on='A', how='inner')
```

- **拼接**： 使用 `concat()` 可以在行或列方向上拼接多个 DataFrame。

```python
df3 = pd.DataFrame({'A': [7, 8], 'B': [9, 10]})
df_combined = pd.concat([df1, df3], axis=0)  # 按行拼接
```

- **连接**： 使用 `join()` 基于索引进行连接。

```python
df1.set_index('A').join(df2.set_index('A'))
```

