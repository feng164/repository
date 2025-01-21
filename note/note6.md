# 推导式

## 一.列表推导式

- ###  语法:

  - ```python
    [表达式 for item in 可迭代对象]
    或 [表达式 for item in 可迭代对象 if 条件判断]
    ```

- ### 示例:

  - ```python
    a=[x for x in range(1,5)]
    print(a)
    #[1,2,3,4]
    
    b=[x*2 for x in range(1,20) if x%5==0]
    print(b)
    #[10,20,30
    
    cells = [(row,col) for row,col in zip(range(1,10),range(101,110))]
    print(cells)
    #[(1,101),(2,102),...,(9,109)]
    ```

- #### 集合推导式类似, 用`{}`

  

## 二.字典推导式

- ### 语法:

  - ```python
    {key表达式:value表达式 for 表达式 in 可迭代对象}
    ```

- ### 示例:

  - ```python
    values=["北京","上海","广州"]
    cities = {id*100:city for id,city in zip(range(1,4),values)}
    print(cities)
    #{100:'北京',200:'上海',300:'广州'}
    
    test=' abcccd effa'
    char_count = {c:test.count(c) for c in test}
    print(char_count)
    #{' ':2,'a':2,'b':1,'c':3,'d':1,'e':1,'f':2}
    ```



## 三.生成器推导式

- #### 不直接生成元组

- ```python
  (x for x in range(1,100) if x%9==0)
  #<generator object <genexpr> at 0x0000020D120024D0>
  ```

- 提示的是“一个生成器对象” , 元组没有推导式

- 一个生成器只能运行一次. 第一次可以得到数据, 第二次就没有了



