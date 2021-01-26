# TASK3

**练习题**：

1、猜数字游戏

题目描述:

电脑产生一个零到100之间的随机数字，然后让用户来猜，如果用户猜的数字比这个数字大，提示太大，否则提示太小，当用户正好猜中电脑会提示，"恭喜你猜到了这个数是......"。在用户每次猜测之前程序会输出用户是第几次猜测，如果用户输入的根本不是一个数字，程序会告诉用户"输入无效"。

(尝试使用try catch异常处理结构对输入情况进行处理)

获取随机数采用random模块。

[![img](https://camo.githubusercontent.com/36da3ff104b2024d86e2a32494facb8f5657f6e9aeced17ef684217ccd5dd1e9/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343233303831393139332e706e67)](https://camo.githubusercontent.com/36da3ff104b2024d86e2a32494facb8f5657f6e9aeced17ef684217ccd5dd1e9/68747470733a2f2f696d672d626c6f672e6373646e696d672e636e2f32303230303731343233303831393139332e706e67)



```python
import random

computer = random.randint(0, 101)
user = 0
while True:
    try:
        user = int(input("请输入你猜的数字"))
    except ValueError:
        print("输入无效")
        continue
    if user == computer:
        print(f'恭喜你猜到了这个数字是{computer}')
    elif user > computer:
        print("太大")
    else:
        print("太小")
   
```