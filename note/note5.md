# 数据容器

## 列表(list)

 ### 1.列表的定义:

- 基本语法

  ```Python
  #字面量
  [元素1,元素2,元素3,...]
  
  #定义变量
  变量名称 = [元素1,元素2,元素3,...]
  
  #定义空列表
  变量名称 = []
  变量名称 = list()
  ```

  - 列表内每一个数据成为元素, 以`[]`作为标识, 每个元素用`,`隔开
  - 列表可以一次存储多个数据, 且可以为不同的数据类型, 支持嵌套

- 特点:

  - 可以容纳最多`2**63-1`个元素
  - 可以容纳不同类型的元素
  - 有下标序号
  - ==允许重复数据==
  - 可以修改(动态的)


### 2.列表的下标索引

- 列表中的每一个元素, 其位置都有下标索引.

  - 从前往后的方向, ==从0开始==依次递增
  - 从后往前的方向,==从-1开始==一次递减

- 如果是嵌套列表, 则使用二维索引

  ```Python
  list=[[1,2,3],[4,5,6]]
  
  #获取内层第一个list
  print(list[0])   #结果: [1,2,3]
  
  #获取内层第一个list的第一个元素
  print(list[0][0])  #结果: 1
  ```

### 3.列表的常用操作

- 功能: 查询, 插入元素, 删除元素, 清空列表, 修改元素, 统计元素个数. 统称为==列表的方法==

  - 查询功能

    - (1)查找制定元素在列表的下标, 如果找不到, 报错`ValueError`

      - 语法: ==列表名.index(“内容”)==

      - ```python
        list=["a","b","c"]
        print(list.index("b"))  #结果: 1
        ```

    - (2)统计列表内有多少元素

      - 语法: ==len(列表)==

      - ```Python
        list = [1,2,3,4,5]
        print(len(list))  #结果: 5
        ```

  - 修改功能

    - 修改特定位置的元素值

    - 语法: ==列表名[下标]=值==

    - ```Python
      #正向下标
      list = [1,2,3]
      list[0] = 5
      print(list)  #结果: [5,2,3]
      
      #反向下标
      list = [1,2,3]
      list[-3] = 5
      print(list)  #结果: [5,2,3]
      ```

  - 插入元素

    - 语法: ==列表名.insert(下标,元素)== , 在指定下标位置插入指定元素

    - ```Python
      list = [1,2,3]
      list.insert(1,"a")
      print(list)  #结果: [1,"a",3]
      ```

  - 追加元素1

    - 语法: ==列表名.append(元素)== , 将指定元素追加到列表的**尾部**

    - ```python
      list=[1,2,3]
      list.append(4)
      print(list)  #结果: [1,2,3,4]
      
      list=[1,2,3]
      list.append([4,5,6])
      print(list)  #结果: [1,2,3,[4,5,6]]
      ```

  - 追加元素2

    - 语法: ==列表名.extend(其他数据容器)== , **将其它数据容器的内容取出**, 依次追加到列表尾部

    - ```Python
      list = [1,2,3]
      list.extend([4,5,6])
      print(list)  #结果: [1,2,3,4,5,6]
      ```

  - 普通删除元素

    - 语法1: ==del+**空格**+列表名[下标]==

    - 语法2: ==列表名.pop(下标)==

    - ```Python
      list = [1,2,3]
      
      #语法1
      del list[0]
      print(list) #结果: [2,3]
      #语法2
      list.pop(0)
      print(list) #结果: [2,3]
      ```

  - 特殊删除元素

    - 删除某元素在列表中的**第一个**匹配项

      - 语法: ==列表名.remove(元素)==

      - ```Python
        list = [1,2,3,2,3]
        list.remove(2)
        print(list)  #结果: [1,3,2,3]
        ```

    - 清空列表内容

      - 语法: ==列表名.clear()==

      - ```Python
        list = [1,2,3]
        list.clear()
        print(list)  #结果: []
        ```

    - 统计某元素在列表内的数量

      - 语法: ==列表名.count(元素)==

      - ```python
        list = [1,1,1,2,3]
        printf(list.count(1)) #结果: 3
        ```

- ![image-20241203193902681](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241203193902681.png)

- ### 4.列表的遍历

  - while

    - ```python
      index = 0
      while index<len(列表):
          元素=列表[index]
          index+=1
      ```

  - for

    - ```Python
      list=[1,2,3]
      for i in list:
          print(i)
      #结果:
      1
      2
      3
      ```

## 元组(tuple)

### 1.元组的定义

- 元组与列表一样,都是可以封装多个、不同类型的元素在内, 但最大的不同是==元组一旦定义完成,就不可修改==

- 用`()`小括号定义元组, 用`,`隔开各个数据, 数据不可以变

  ```Python
  #定义元祖字面量
  (元素1,元素2,...)
  #定义元祖变量
  变量名称 =(元素1,元素2,...)
  #定义空元组
  变量名称=()           #方式1
  变量名称=tuple()      #方式2
  ```

- 元组也支持嵌套:

  - ```Python
    #定义一个嵌套元组
    t1=((1,2,3),(4,5,6))
    print(t[0][0]) #结果: 1
    ```

- 注意事项

- ```python
  #定义3个元素的元组
  t1 = (1,'hello', True)
  
  #定义1个元素的元组
  t2 = ('Hello',)  #注意: 必须带有括号,否则不是元组类型,而是函数类型
  ```

- ==**注意: 元组只有一个数据时这个数据后面要加`,`**==

### 2.元组的相关操作(语法与列表一样)

- `index()`
- `count()`
- `len(元组)`

### 3.元组的相关操作注意事项

- 不可以修改元组内容

- 可以修改元组内list的内容

  - ```python
    #尝试修改元组内容
    t1 = (1,2,['a','b'])
    t1[2][1] = 'c'
    print(t1) #结果: (1,2,['a','c'])
    ```

- 不可以替换list为其它list或其他类型

### 4.元组的特点

- 可以容纳多个,多种数据
- 数据是有序存储的
- 允许重复数据
- **不可以修改**

## 字符串(string)

- 字符串是一个==无法修改==的数据容器, 和*元组*一样

- 字符串的常用操作

  - (1)查找特定字符串的下标索引

    - ==字符串.index(字符串)==

    - ```python
      str = "itcast and itheima"
      print(str.index("and")) #结果 7(and的第一个字母'a'在字符串第7个位置)
      ```

  - (2)字符串的替换, 将字符串1全部替换为字符串2(**右换左**)

    - ==字符串.replace(字符串1,字符串2)==

    - 注意: **不是修改字符串本身, 而是得到了一个新字符串**

    - ```Python
      name = "itcast itheima"
      new_name = name.replace("it", "G")
      print(new_name)	#结果: Gcast Gheima
      print(name) #结果:itcast itheima
      ```

  - (3)字符串的分割

    - ==字符串.split(分隔符字符串)==

    - 功能: 按照指定的分隔符字符串, 将字符串划分为多个字符串, 并存入**列表对象**中

    - 注意: ==字符串本身不变, 而是得到了一个列表对象==

    - ```Python
      name = "today is a good day"
      name_list = name.split(" ")
      print(name_list) #结果: ['todat','is','a','good','day']
      print(type(name_list)) #结果:<class 'list'>
      ```

  - (4)字符串的规整操作(去前后指定字符串)

    - ==字符串.strip(字符串) / 字符串.strip()==

    - ```python
      str = "12itheima and itcast21"
      print(str.strip("12")) #结果: "itheima and itcast"
      
      str = " itheima and itcast "
      #strip()  括号里不加东西则去除首位空白
      print(str.strip())  #结果:"itheima and itcast"
      ```

    - **注意**: 传入的是“12”, 其实就是“1”和“2”都移除, 是**按照单个字符**

  - (5)统计字符串中某字符串的*次数*

    - ==字符串.count(字符串)==

    - ```python
      str = "itheima and itcast"
      print(str.count("it"))  #结果: 2
      ```

  - (6)统计字符串的长度

    - ==len(字符串)==

    - ```Python
      str = "1234 abcd ABCD"
      print(len(str)) #结果: 20
      ```

    - 注意: **空格也算一个字符**

- ![image-20241206215910120](C:\Users\cai\AppData\Roaming\Typora\typora-user-images\image-20241206215910120.png)



## 切片

- **列表, 元组, 字符串**均可以视作*序列*

- 切片是从一个序列中取出一个子序列

- 序列**`[起始下标:结束下标:步长]`**

  - 起始下标有被包含, **留空视作从头开始**

  - ==结束下标没有被包含==, **留空视作截取到结尾**

  - 步长表示取元素的间隔, 步长为负数表示反向取(此时起始和反向下标都要标记)

  - 此操作只会得到*新的序列*

  - ```Python
    # 定义一个列表
    my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
    # 切片操作：从索引1开始到索引5结束（不包括索引5）
    print("切片1:", my_list[1:5])
    #结果: [2,3,4,5,6]
    
    # 切片操作：从索引1开始到列表末尾
    print("切片2:", my_list[1:])
    #结果: [ 2, 3, 4, 5, 6, 7, 8, 9,10]
    
    # 切片操作：从列表开始到索引5结束（不包括索引5）
    print("切片3:", my_list[:5])
    #结果: [1,2,3,4,5]
    
    # 切片操作：从列表末尾到索引5结束（不包括索引5），步长为-1
    print("切片4:", my_list[-5:-1:-1])
    #结果: [10,9,8,]
    
    # 切片操作：从索引3开始，步长为2
    print("切片5:", my_list[3::2])
    #     [4, 6, 8, 10]
    
    # 切片操作：从索引6开始，步长为-2
    print("切片6:", my_list[6::-2])
    #      [7, 5, 3, 1]
    # 字符串切片操作
    my_string = "Hello, World!"
    # 从索引1开始到索引5结束（不包括索引5）
    print("字符串切片:", my_string[1:5])
    #   字符串切片: ello
    
    # 元组切片操作
    my_tuple = (11, 12, 13, 14, 15)
    # 从索引1开始到索引3结束（不包括索引3）
    print("元组切片:", my_tuple[1:3])
    #  元组切片: (12, 13)
    ```

  

## 集合(set)

- 特点:**去重**, **无序**

- ```python
  #定义集合字面量
  {元素1,元素2,...}
  
  #定义集合变量
  变量名称 = {元素1,元素2,...}
  
  #定义空集合
  变量名称 = set()
  ```

- 功能

  - 添加新元素

    - ==集合.add(元素)==

    - ```python
      set1 = {"hello","world"}
      set1.add("search")
      print(set1) #结果: {'hello','world','search'}
      ```

  - 移除元素

    - ==集合.remove(元素)==

    - ```python
      set1 = {"hello","world"}
      set1.remove("hello")
      print(set1)#结果: {'world'}
      ```

  - 从集合中*随机*取出元素

    - ==集合.pop()==

    - ```python
      set1 = {"hello","world","search"}
      element = set1.pop()
      print(set1)      #结果: {'world','search'}
      print(element)  #结果: 'hello'
      #每次结果不同
      ```

  - 清空结合

    - ==集合.clear()==

    - ```python
      set1 = {"hello","world"}
      set1.clear()
      print(set1) #结果: set() 空集合
      ```

  - 取出2个集合的差集(集合1有而集合2没有的)

    - ==集合1.difference(集合2)==

    - ```python
      set1() = {1,2,3}
      set2() = {1,5,6}
      set3 = set1.difference(set2)
      print(set3) #结果: {2,3}
      print(set1) #结果: {1,2,3}不变
      print(set2) #结果: {1,5,6}不变
      ```

  - 消除2个集合的差集(在集合1内消除与集合2相同的元素)

    - ==集合1.difference_update(集合2)==

    - ```Python
      set1 = {1,2,3}
      set2 = {1,5,6}
      set1.difference_update(set2)
      print(set1) #结果: {2.3}
      print(set2) #结果: {1,5,6}
      ```

  - 2个集合合并

    - ==集合1.union(集合2)==

    - ```python
      set1 = {1,2,3}
      set2 = {1,5,6}
      set3 = set1.union(set2)
      print(set3) #结果: {1,2,3,5,6} 重复的归为一个
      print(set1) #结果: {1,2,3} 不变
      print(set2) #结果: {1,5,6} 不变
      ```

  - 查看集合的元素数量

    - ==len(集合)==

    - ```python
      set1 = {1,2,3}
      print(len(set1)) #结果: 3
      ```

- 注意: 因为集合不支持下标索引, 所以不支持while循环, 可以用**for循环**

- ![image-20241207144615098](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241207144615098.png)


## 字典(dictionary)

### 1.定义

- 同样使用`{}`,不过存储的元素是一个对一个的,即**键值对(Key-Value)**, 键值间用`:`分隔, 键值对间用`,`分隔

- Key和Value可以是任意类型的数据(==key不可以是字典==)

- key不可以重复

  - 语法

  - ```Python
    #定义字典字面量
    {key1:value1 , key2:value2,...}
    #定义字典变量
    my_dict = {key1:value1 , key2:value2,...}
    #定义空字典
    my_dict = {}
    my_dict = 
    dict()
    ```

 ### 2.字典数据的和获取

- 字典不可以用下标索引, 但可以通过key值来获取对应的value

  - ==字典[“key”]== , 注意用的是`[]`

  - ```python
    personal_information = {"name":joker ,"age":18 ,"birthday_year":2006 }
    print(personal_information["name"])
    #结果:joker
    print(personal_information["age"]) 
    #结果: 18
    print(personal_information["birthday_year"]) #结果: 2006 
    ```

### 3.字典的嵌套

- 定义

  - ```python
    person_information = {
      "keqing":{"语文":77 , "数学":66},
      "keqlng":{"语文":88 , "数学":87},
      "keping":{"语文":99 , "数学":96}
    }
    print(person_information["keqing"])
    #结果: {"语文":77, "数学":66}
    print(person_iinformation["keqing"]["语文"])
    #结果: 77
    print(person_information["keqlng"]["数学"])
    #结果: 86
    ```

### 4.字典的常用操作

- 新增元素

  - ==字典[Key] = value==

  - ```Python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    score["d"] = 10
    print(score) #结果:{'a':7,'b':9,'c':8,'d':10}
    ```

- 更新元素

  - ==字典[Key] = Value==

  - 因为Key不可以重复, 所以对已存在的Key执行上述操作, 就是更新Value (覆盖)

  - ```python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    score["a"] = 10
    print(score) #结果:{'a':10,'b':9,'c':8}
    ```

- 删除元素

  - ==字典.pop(Key)==  , 获得指定key的value, 同时原字典被修改

  - ```python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    value = score.pop("a")
    print(value) #结果: 7
    print(score) #结果: {'b':9,'c':8}
    ```

- 清空字典

  - ==字典.clear()==

  - ```python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    score.clear()
    print(score) #结果:  {}
    ```

- 获取全部的key

  - ==字典.keys()==

  - ```Python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    keys = score.keys()
    print(keys) #结果: dict_keys(['a','b','c'])
    ```

- 遍历字典

  - ==for key in 字典.keys()==

  - ```Python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    keys = score.keys()
    for key in keys:
        print(f"人:[key], 分数:{score[key]}")
    #结果:
    人:a, 分数:7
    人:b, 分数:9
    人:c, 分数:8
    ```

- 计算字典内全部元素中键值对的数量

  - ==len(字典)==

  - ```python
    score = {
        "a":7,
        "b":9,
        "c":8
    }
    print(len(score)) #结果: 3
    ```

  ![image-20241208115936230](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241208115936230.png)

## 多种数据容器对比

![image-20241208120413584](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241208120413584.png)

## 数据容器的通用操作

### 1.遍历

- 5类都支持`for`
- 集合和字典不支持`while` (不支持下标索引)

### 2.统计

- `len(容器)`
- `max(容器)`
- `min(容器)`

### 3.通用转换功能

- `list(容器)`
- `str(容器)`
- `tuple(容器)`
- `set(容器)`

### 4.通用排序功能

sorted(容器,[reverse=True]) : 给容器倒序排序且**不改变原容器排序**

```Python
# 定义一个列表
original_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]

# 打印原始列表
print("原始列表:")
print(original_list)

# 使用sorted函数对列表进行排序，sorted返回一个新的列表，原始列表不变
sorted_list = sorted(original_list)
print("排序后的列表（升序）:")
print(sorted_list)

# 检查原始列表是否改变
print("原始列表是否改变（应该输出False）:")
print(original_list is sorted_list)

# 使用sorted函数对列表进行降序排序
sorted_list_reverse = sorted(original_list, reverse=True)
print("排序后的列表（降序）:")
print(sorted_list_reverse)

#原始列表:
#[3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
#排序后的列表（升序）:
#[1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
#原始列表是否改变（应该输出False）:
#False
#排序后的列表（降序）:
#[9, 6, 5, 5, 5, 4, 3, 3, 2, 1, 1]
```

![image-20241208121956286](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241208121956286.png)



## zip()函数

- #### 1.`zip()` 是 Python 中的一个内置函数，它可以将多个可迭代对象（如列表、元组、字符串等）中的元素一一对应地“压缩”在一起，返回一个由元组组成的迭代器。每个元组包含来自所有可迭代对象中的对应位置的元素

- #### 2.语法:

  - ```python
    zip(iterable1,iterable2,...,iterableN)
    ```

  - #### 返回值: 返回一个 `zip` 对象，它是一个迭代器，包含由元组组成的元素。每个元组由输入迭代器中的对应元素组成

- #### 3.示例:

  - #### 1. 两个列表合并：

    ```python
    list1 = [1, 2, 3]
    list2 = ['a', 'b', 'c']
    
    result = zip(list1, list2)
    print(list(result))  # 输出: [(1, 'a'), (2, 'b'), (3, 'c')]
    ```

   - #### 2. 不同长度的列表：

    如果输入的可迭代对象长度不一致，`zip()` 会按**最短**的那个可迭  代对象的长度来生成元组：

    ```python
  list1 = [1, 2, 3, 4]
  list2 = ['a', 'b']
  
  result = zip(list1, list2)
  print(list(result))  # 输出: [(1, 'a'), (2, 'b')]
    ```

   - #### 3. 解压操作：

    也可以使用 `zip()` 来进行解压操作，使用 `*` 运算符：

    ```python
  zipped = [(1, 'a'), (2, 'b'), (3, 'c')]
  list1, list2 = zip(*zipped)
  print(list1)  # 输出: (1, 2, 3)
  print(list2)  # 输出: ('a', 'b', 'c')
    ```

   - #### 4. 使用 `zip` 进行字典的创建：

    ```python
  keys = ['name', 'age', 'city']
  values = ['Alice', 30, 'New York']
  
  result = dict(zip(keys, values))
  print(result)  # 输出: {'name': 'Alice', 'age': 30, 'city': 'New York'}
    ```