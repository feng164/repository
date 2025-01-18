# 函数

## 1.函数的定义

- 语句

  - ```Python
    def 函数名(传入参数):
        函数体
        return 返回值
    ```

    - 参数如果不需要,可以省略
    - 返回值如果不需要,可以省略
    - 函数必须先定义后使用

## 2.函数的参数

- 传入参数

  - ```Python
    def add(x,y):
        result=x+y
        print(f"{result}")
    
    add(5,6)
    ```

  - 上述例子中, x和y为形参 ,参数间用`,`隔开; 5和6为实参, 传入的时候, ==按照顺序传入==, 用`,`隔开

## 3.函数的返回值

- 定义: 程序中函数完成事情后,最后给调用者的结果

  - 语法

    ```Python
    def 函数(参数):
      函数体
      return 返回值
    变量=函数(参数)
    ```

- None类型

  - Python中的一个特殊字面量,一个函数无返回值,实际上是返回了None. None可以主动使用return返回, 效果等同于不写return语句
  - 应用场景
    - 用在函数无返回值上
    - 用在if判断上
      - if中, None等同于false
      - 一般用于在函数中主动返回None, 配合if判断做相关处理
    - 用于声明无内容的变量上

## 4.函数的说明文档

- 语法

  ```Python
  def func(x,y):
      """
      函数说明
      :param x: 形参x的说明
      :param y: 形参y的说明
      :return: 返回值的说明
      """
      函数体
      return 返回值
  ```

- pycharm中, 可以通过鼠标悬停,查看调用函数的说明文档

  ![image-20241202195101551](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241202195101551.png)

## 5.函数的嵌套调用

- 一个函数里面又调用了另外一个函数

## 6.变量的作用域

- 变量分为两种: 局部变量和全局变量

  - 局部变量是定义在函数体内部的对象,即只在函数体内部生效, 作用: 在函数体内部,临时保存数据, 即当函数调用完成后, 则销毁局部变量

  - 全局变量是在函数体内外都能生效的变量

  - `global`关键字, 可以在函数体内部改变全局变量的值

    - ```Python
      num=100
      def testa():
          print(num)
          
      def testb():
          #global 关键字声明num是全局变量
          global num
          num = 200
          print(num)
          
      testa()  #结果: 100
      testb()  #结果: 200
      print(f"此时的num的值为{num}") #结果: 200
      ```

      



# 函数进阶

## 一.函数多返回值

- ```python
  def test_return():
      return 1,2
  
  x,y = test_return()
  print(x) #结果1
  print(y) #结果2
  ```

- 按照返回值的顺序, 写对应顺序的多个变量接收即可

- 变量之间用逗号隔开

- 支持不同类型的数据`return`

## 二.函数多种传参方式

- 函数的参数种类

  1. 位置参数: 调用函数时根据**函数的定义的参数的位置**来传递参数 ; 注意: ==传递的参数和定义的参数的顺序及个数必须一致==

     ```python
     def user_info(name,age,gender):
         print(f'您的名字是{name},年龄是{age},性别是{gender}')
         
     user_info('TOM',20,'male')
     ```

   2. 关键字参数: 通过`“键值对”`形式传递参数 ; 注意:==函数调用时, 如果有位置参数时 , 位置参数必须在关键字参数前面, 但关键字参数之间不存在先后顺序==

      ```Python
      def user_info(name,age,gender):
          print(f"您的名字是{name},年龄是{age},性别是{gender}")
          
      #关键字传参
      user_info(name="小明",age=20,gender="男")
      #可以不按照固定顺序
      user_info(age=20,gender="男",name="小明")
      #可以和位置参数混用, 位置参数必须在前, 且匹配参数顺序
      user_info("小明",age=20,gender="男")
      ```

      

   3. 缺省参数

   4. 不定长参数

  