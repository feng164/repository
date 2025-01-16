# 基础语法与缩进

## 一.基础语法

### 1.字面量

| 类型             | 描述                         | 说明                                    |
| ---------------- | ---------------------------- | --------------------------------------- |
| Number           | 整数,浮点数,复数,布尔        | 复数(complex),如:4+3*j, 以j结尾表示复数 |
| String           | 字符串                       | 由任意数量的字符组成,用双引号包围字符串 |
| List(列表)       | 有序的可变序列               | 使用最频繁的数据类型,可有序记录一堆数据 |
| Tuple(元组)      | 有序的==不可变==序列         | 可有序记录一堆不可变的数据集合          |
| Set(集合)        | ==无序不重复==集合           | 可无序记录一堆不重复数据集合            |
| Dictionary(字典) | 无序==Key-Value==(键-值)集合 | 可无序记录一堆键-值型数据集合           |

### 2.注释

用`#`号表示后面的文字为注释,对代码进行解释

- #### (1)单行注释

  - ```python
    #我是注释
    print("hello")
    ```


- #### (2)多行注释:一对三个双引号

  - ```python
    """"
    	first
    	second
    	third
    """
    print("normal")
    ```

### 3.变量

- 定义:变量就是在程序运行时,记录数据用的
- 格式:变量名=变量值
- 命名:
  - 变量名只能包含==字母、数字和下划线==,不能以*数字*开头
  - 不能包含空格,可以用`_`分隔
  - 不要用关键字命名,如“print”
  - 名字应即简短又有描述性,如`name`比`n`好
  - 慎用大小写,==变量名全用小写==

### 4.数据类型

- `字符串`,`整形`,`浮点型`…

- type()语句

  - (1)在print语句中直接输出类型信息

    - ```python
      print(type(666))
      print(type(3.14))
      ```

      输出结果:

    - ```python
      <class 'int'>
      <class 'float'>
      ```


  - (2)用变量存储

    - ```python
      int_type=type(666)
      print(int_type)
      ```

### 5.字符串定义方式

- 双引号定义法: `text_1=“我是字符串”`

- 单引号定义法: `text_2=‘我是字符串’`

- 三引号定义法: `text_3=“”“我是字符串”“”`

  

### 6.数据类型转换

- 语句:

  - `int(x)`
  - `float(x)`
  - `str(x)`

- (1)任何类型,都可以通过`str()`转换成字符串

- (2)字符串内必须是真数字,才可以将字符串转换为数字

  

### 7.运算符

- 算术运算符

![image-20241201093358677](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241201093358677.png)

```python
print("2的3次方是:%d" %(2**3))
```

- 赋值运算符: `=`

- 复合赋值运算符

  ![image-20241201093636271](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241201093636271.png)

- 位运算符

  | 符号   | 含义               |
  | ------ | ------------------ |
  | ~      | 按位取反运算符     |
  | <<, >> | 左移、右移位运算符 |
  | &      | 按位与运算符       |
  | ^      | 按位异或运算符     |
  | \|     | 按位或运算符       |


- 逻辑运算符

  | 符号 | 含义   |
  | ---- | ------ |
  | not  | 逻辑非 |
  | and  | 逻辑与 |
  | or   | 逻辑或 |

- 比较运算符

  `<=`, `<`, `>`, `>=`, `!=`, `==`, `is`, `is not`, `in`, `not in`,`<>`, `!=`, `==`

- ==优先级==(从上到下递减)

  - `**`
  - `~` 
  - `*`, `/`, `//`, `%` 
  - `+`, `-` 
  - `<<`, `>>` 
  - `&`
  - `^` 
  - `|` 
  - `<=`, `<`, `>`, `>=`, `!=`, `==`, `is`, `is not`, `in`, `not in` 
  - `<>`, `!=`, `==` - 等于运算符（`<>` 是Python 2中的写法，Python 3中使用 `!=`）
  - `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`, `&=`, `^=`, `|=` 
  - `not`
  - `and` 
  - `or` 

  - 当运算符优先级相同时，表达式会从左到右进行计算。如果需要改变运算顺序，可以使用括号`()`来明确指定。

### 8.字符串扩展

- (1)字符串的引号嵌套: 定义的字符串本身包含单引号,双引号自身

  - 单引号定义法: 内含双引号

    ```python
    single_quoted = 'He said, "Hello, world!"'
    print(single_quoted)  
    # 输出: He said, "Hello, world!"
    ```

  - 双引号定义法: 内含单引号

    ```python
    double_quoted = "She asked, 'What's your name?'"
    print(double_quoted) 
    # 输出: She asked, 'What's your name?'
    ```

  - 用转义字符`\`来将引号解除效用,变成普通字符串

    ```python
    escaped_single = "He said, \"Hello, world!\""
    print(escaped_single)  
    # 输出: He said, "Hello, world!"
    
    escaped_double = 'She asked, \'What\'s your name?\''
    print(escaped_double)  
    # 输出: She asked, 'What's your name?'
    ```

- (2)字符串的拼接 :用`+`来拼接

  - ```python
    language="python"
    print("I am learning" + language + ",which is interesting.")
    #输出  I am learning python,which is interesting.
    ```

  - ==字符串无法与非字符串拼接==, 因为类型不一样

- (3)字符串格式化1

  - ```python
    language="python"
    message="I love %s" % language
    #输出  I love python
    ```

  - 其中`%`表示占位,`s`表示将变量变成字符串放入占位的地方

  - ```python
    age=18
    name=joke
    print("I am %s ,my age is %d" % (name,age))
    #输出 I am joke, my age is 18
    ```

  - 多个变量占位,变量要用括号括起来,并按照==占位顺序==填入

  - `%s`:字符串   `%d`:整数    `%f`:浮点数

- (4)格式化的精度控制

  - 用`m.n`的格式来控制

    - m: 控制宽度, 要求是数字, 宽度小于数字长度时不生效(很少使用)
    - 你: 控制小数点精度, 要求是数字, 会进行小数的四舍五入

  - 例如:

    - `%5.2f`:  表示将宽度控制为5, 将小数点精度设置为2

    - `%.2f`:  不限制宽度,只设置精度

    - ```python
      num1=11
      num2=11.345
      print("%5d" % num1)
      print("%7.2f" % num2)
      print("%.2f" % num2)
      #输出
      #   11(前面3个空格,5-2=3)
      #  11.35(前面2个空格,.也算一个位置,0.345->0.35)
      #11.35
      ```

- (5)字符串格式化方式2

  - 语法: `f"内容{变量}"` 的格式来快速格式化, 不能控制精度

  - ```python
    name=jack
    age=18
    height=1.76
    print(f"我是{name},我的年龄是{age},我的身高是{height}m")
    #输出 我是Jack,我的年龄是18,我的身高是1.76m(没控制精度,照常输出)
    ```

- (6)对表达式进行格式化

  - ```python
    print("1*1的结果是:%d" % (1*1))
    print(f"1*1的结果是:{1*1}")
    #上述两种方法都可以
    ```

### 9.数据输入

- `input()` 语句, 但是无论键盘输入什么, 最终结果都是==字符串类型==的数据

  ```python
  name=input("tell me your name:")
  print("get it.your name is %s" % name)
  #输入  tell me your name: gekdner
  #     get it.your name is gekdner
  ```

  
