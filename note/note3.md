# 循环语句

## 1.`while`循环

- 语句

 ```Python
 a=3
 while a>=1 :
     print(f"{a}")
     a-=1
 #输出
 3
 2
 1
 ```



## 2.`for`循环

- (1)语法:

  `for` 临时变量 `in` 待处理数据集

  - 例子:

    ```Python
    name="inter"
    for x in name:
      print(x)
    #输出
    i
    n
    t
    e
    r
    ```

- (2)range语句

  - 语法中,待处理数据集严格来说称之为==可迭代类型==
    - 包括: 字符串, 列表, 元组…
  - 语法1: `range(number)`: 获取从0开始到number结束的数字序列==(不含number本身)==
  - 语法2: `range(num1,num2)`: 获取区间`[num1,num2)`之间的数字
  - 语法3:`range(num1,num2,step)` , step为步长,默认为1
    - 如range(5,10,2)得[5,7,9]

- (3)变量作用域

  - 如上方的`x`是临时变量, 在编程规范上(非强制限定), 作用范围只限定在for循环内部
  - 如需访问临时变量,可以先在循环外定义它

## 3.循环中断

- (1)`continue`
  - 用于中断本次循环(它所在的循环 ,如果存在嵌套循环, 它在哪就中断哪层循环), 直接进入下一循环
  - ![image-20241201164659945](https://typora10213.oss-cn-guangzhou.aliyuncs.com/undefinedimage-20241201164659945.png)
- (2)break
  - 直接结束所在循环, 永久中断



