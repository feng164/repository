# 判断语句

## 1.布尔类型和比较运算符

### 1.布尔类型:

- true表示真,值为1
- false表示假,值为0

### 2.比较运算符的使用

```python
result1=10>5
result2=10<5
result3="it"=="ut"
print(f"{result1},{type(result1)},{result2},{type(result2)},{result3},{type(result3)}")
#输出 True,<class 'bool'>,False,<class 'bool'>,False,<class 'bool'>
```

### 3.`if` `else` `elif`语句

- (1)if

  - if 条件 ==:==   (当条件为真才执行)
  - [缩进] 语句			

- (2)else

  - else ==:==    (条件为假时执行)
  - [缩进] 语句

- (3)`elif`

  - 可以写多个, 介于if和else之间, 最后的else可以不写

- ```python
  # 获取用户输入的分数
  score = float(input("请输入你的分数（0-100）："))
  
  # 根据分数判断成绩
  if score >= 90:
      print("优秀")
  elif score >= 80:
      print("良好")
  elif score >= 70:
      print("中等")
  elif score >= 60:
      print("及格")
  else:
      print("不及格")
  ```

  

### 4.判断语句的嵌套

```Python
# 获取用户输入的分数和年龄
score = float(input("请输入你的分数（0-100）："))
age = int(input("请输入你的年龄："))

# 判断成绩等级
if score >= 90:
    print("成绩等级：优秀")
    # 成绩优秀时，进一步判断年龄
    if age >= 18:
        print("有资格申请成人优秀奖学金")
    else:
        print("有资格申请青少年优秀奖学金")
elif score >= 80:
    print("成绩等级：良好")
    # 成绩良好时，根据年龄判断是否有资格获得进步奖学金
    if age >= 16:
        print("有资格申请进步奖学金")
else:
    print("成绩等级：普通")
    # 成绩普通时，根据年龄判断是否有资格获得鼓励奖学金
    if age >= 14:
        print("有资格申请鼓励奖学金")
```



