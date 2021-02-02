# TASK7

## 类与对象

### 练习题：

1、以下类定义中哪些是类属性，哪些是实例属性？

```python
class C:
    num = 0  # 类属性
    def __init__(self):
        self.x = 4  # 实例属性
        self.y = 5  # 实例属性
        C.count = 6  # 类属性
```

2、怎么定义私有⽅法？

函数名前加两个下划线'__'

3、尝试执行以下代码，并解释错误原因：

```python
class C:
    def myFun():
        print('Hello!')
    c = C()  
    c.myFun()
```

①没有self，代码不知道该调用谁

②第四五行代码应该顶格书写，如果像这样缩进书写，就意味着在C内部定义了实例。

4、按照以下要求定义一个游乐园门票的类，并尝试计算2个成人+1个小孩平日票价。

要求:

- 平日票价100元
- 周末票价为平日的120%
- 儿童票半价

```python
class Ticket(object):
    def __init__(self, kind, time, count):
        self.price = 0
        self.kind = kind
        self.time = time
        self.count = count

    def get_ticket_price(self):
        if self.kind == '儿童':
            if self.time == '平日':
                self.price = 50
            else:
                self.price = 60
        if self.kind == '成人':
            if self.time == '平日':
                self.price = 100
            else:
                self.price = 120
        return self.price * self.count


ticket1 = Ticket('成人', '平日', 2)
ticket2 = Ticket('儿童', '平日', 1)
print(ticket1.get_ticket_price()+ticket2.get_ticket_price())

```

## 魔法方法

### 练习题：

1、上面提到了许多魔法方法，如`__new__`,`__init__`, `__str__`,`__rstr__`,`__getitem__`,`__setitem__`等等，请总结它们各自的使用方法。

- `__init__(self[, ...])` 构造器，当一个实例被创建的时候调用的初始化方法

- `__new__(cls[, ...])`

  在一个对象实例化的时候所调用的第一个方法，在调用

  ```
  __init__
  ```

  初始化前，先调用

  ```
  __new__
  ```

- `__del__(self)` 析构器，当一个对象将要被系统回收之时调用的方法。

- ```
  __str__(self)
  ```

  - 当你打印一个对象的时候，触发`__str__`
  - 当你使用`%s`格式化的时候，触发`__str__`
  - `str`强转数据类型的时候，触发`__str__`

- ```
  __repr__(self)
  ```

  - `repr`是`str`的备胎
  - 有`__str__`的时候执行`__str__`,没有实现`__str__`的时候，执行`__repr__`
  - `repr(obj)`内置函数对应的结果是`__repr__`的返回值
  - 当你使用`%r`格式化的时候 触发`__repr__`

- `__add__(self, other)`定义加法的行为：`+`
- `__sub__(self, other)`定义减法的行为：`-`

- `__mul__(self, other)`定义乘法的行为：`*`
- `__truediv__(self, other)`定义真除法的行为：`/`
- `__floordiv__(self, other)`定义整数除法的行为：`//`
- `__mod__(self, other)` 定义取模算法的行为：`%`
- `__divmod__(self, other)`定义当被 `divmod()` 调用时的行为
- `divmod(a, b)`把除数和余数运算结果结合起来，返回一个包含商和余数的元组`(a // b, a % b)`。

- `__pow__(self, other[, module])`定义当被 `power()` 调用或 `**` 运算时的行为

- `__lshift__(self, other)`定义按位左移位的行为：`<<`

- `__rshift__(self, other)`定义按位右移位的行为：`>>`

- `__and__(self, other)`定义按位与操作的行为：`&`

- `__xor__(self, other)`定义按位异或操作的行为：`^`

- `__or__(self, other)`定义按位或操作的行为：`|`

  

- `__radd__(self, other)`定义加法的行为：`+`
- `__rsub__(self, other)`定义减法的行为：`-`
- `__rmul__(self, other)`定义乘法的行为：`*`
- `__rtruediv__(self, other)`定义真除法的行为：`/`
- `__rfloordiv__(self, other)`定义整数除法的行为：`//`
- `__rmod__(self, other)` 定义取模算法的行为：`%`
- `__rdivmod__(self, other)`定义当被 divmod() 调用时的行为
- `__rpow__(self, other[, module])`定义当被 power() 调用或 `**` 运算时的行为
- `__rlshift__(self, other)`定义按位左移位的行为：`<<`
- `__rrshift__(self, other)`定义按位右移位的行为：`>>`
- `__rand__(self, other)`定义按位与操作的行为：`&`
- `__rxor__(self, other)`定义按位异或操作的行为：`^`
- `__ror__(self, other)`定义按位或操作的行为：`|`



- `__neg__(self)`定义正号的行为：`+x`

- `__pos__(self)`定义负号的行为：`-x`

- `__abs__(self)`定义当被`abs()`调用时的行为

- `__invert__(self)`定义按位求反的行为：`~x`

  

- `__len__(self)`定义当被`len()`调用时的行为（返回容器中元素的个数）。
- `__getitem__(self, key)`定义获取容器中元素的行为，相当于`self[key]`。
- `__setitem__(self, key, value)`定义设置容器中指定元素的行为，相当于`self[key] = value`。
- `__delitem__(self, key)`定义删除容器中指定元素的行为，相当于`del self[key]`。

2、利用python做一个简单的定时器类

要求:

- 定制一个计时器的类。
- `start`和`stop`方法代表启动计时和停止计时。
- 假设计时器对象`t1`，`print(t1)`和直接调用`t1`均显示结果。
- 当计时器未启动或已经停止计时时，调用`stop`方法会给予温馨的提示。
- 两个计时器对象可以进行相加：`t1+t2`。
- 只能使用提供的有限资源完成。

```python
import time


class Timer(object):
    def __init__(self):
        self.start_time = 0
        self.end_time = 0
        self.time = 0
        print('初始时间为0')

    def start(self):
        print('启动计时')
        self.start_time = time.time()
        self.end_time = self.start_time

    def stop(self):
        self.end_time = time.time()
        self.time = self.end_time - self.start_time
        if self.start_time == 0:
            print('计时器未启动')
        elif self.end_time != self.start_time:
            print('已经停止计时')

    def __add__(self, other):
        self.time = self.time + other.time
        return self

    def getresult(self):
        return self.time

    def __str__(self):
        return f'{self.getresult()}'


t1 = Timer()
t2 = Timer()
t1.stop()
t2.stop()
t1.start()
t2.start()
time.sleep(5)
t1.stop()
t2.stop()
print(t1.getresult())
print(t2.getresult())
print((t1 + t2).getresult())
```

> 初始时间为0
> 初始时间为0
> 计时器未启动
> 计时器未启动
> 启动计时
> 启动计时
> 已经停止计时
> 已经停止计时
> 5.000208854675293
> 5.000208854675293
> 10.000417709350586