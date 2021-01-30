# TASK5

## 字典

##### 字典的定义和访问

###### <1> 定义空字典

###### <2> 定义带数据的字典

###### <3> dict.fromkeys(seq[, value])

【例子】

```python
# 字典 dict 使用{}定义，是由键值对组成(key-value)
# 变量 = {key1: value1, key2: value2, ···} 一个key: value 键值对是一个元素
# 字典的 key 可以是 字符串类型和数字类型(int float), 不能是 列表
# value值可以是任意类型

# 1. 定义空字典
my_dict = {}
my_dict1 = dict()
print(my_dict, type(my_dict))
print(my_dict1, type(my_dict1))

# 2. 定义带数据的字典
my_dict2 = {'name': 'isaac', 'age': 18, 'like': ['学习', '购物', '游戏'], 1: [2, 5, 8]}
print(my_dict2)

# 3.dict.fromkeys(seq[, value]) 用于创建一个新字典，以序列 seq 中元素做字典的键，value 为字典所有键对应的初始值。
seq = ('name', 'age', 'sex')
dic1 = dict.fromkeys(seq)
print(dic1)
# {'name': None, 'age': None, 'sex': None}
dic2 = dict.fromkeys(seq, 10)
print(dic2)
# {'name': 10, 'age': 10, 'sex': 10}
dic3 = dict.fromkeys(seq, ('小马', '8', '男'))
print(dic3)
# {'name': ('小马', '8', '男'), 'age': ('小马', '8', '男'), 'sex': ('小马', '8', '男')}
```

###### <1> 使用key访问

###### <2> 使用 字典.get(key[，数据值])访问

###### <3> dict.setdefault(key, default=None)

###### <4> key in/not in dict

```python
# 1.访问 value 值：在字典中没有下标的概念，所以要使用 key 值访问 value 值
# 18
print(my_dict2['age'])
# '购物'
print(my_dict2['like'][1])

# 如果key值不存在
print(my_dict2['gender'])  # 代码报错，因为key值不存在
# 字典.get(key) 如果key值不存在，不会报错，返回的是None
print(my_dict2.get('gender'))

# 2.字典.get(key, 数据值)   如果key存在，返回key对应的value值，如果key不存在，返回书写的数据值
print(my_dict2.get('gender', '男'))  # 男
print(my_dict2.get('age', 1))  # 18

# 3.dict.setdefault(key, default=None)和get()方法 类似, 如果键不存在于字典中，将会添加键并将值设为默认值。
dic = {'Name': 'Lsgogroup', 'Age': 7}
print("Age 键的值为 : %s" % dic.setdefault('Age', None))  # Age 键的值为 : 7
print("Sex 键的值为 : %s" % dic.setdefault('Sex', None))  # Sex 键的值为 : None
print(dic)  
# {'Age': 7, 'Name': 'Lsgogroup', 'Sex': None}

# 4.key in dict操作符用于判断键是否存在于字典中，如果键在字典 dict 里返回true，否则返回false。而not in操作符刚好相反，如果键在字典 dict 里返回false，否则返回true。
dic = {'Name': 'Lsgogroup', 'Age': 7}
# in 检测键 Age 是否存在
if 'Age' in dic:
    print("键 Age 存在")
else:
    print("键 Age 不存在")
# 检测键 Sex 是否存在
if 'Sex' in dic:
    print("键 Sex 存在")
else:
    print("键 Sex 不存在")
# not in 检测键 Age 是否存在
if 'Age' not in dic:
    print("键 Age 不存在")
else:
    print("键 Age 存在")
# 键 Age 存在
# 键 Sex 不存在
# 键 Age 存在

# 字典长度由键值对个数决定，可以由len()计算
print(len(my_dict2))  # 4

```

##### 字典中添加和修改数据

###### <1> 普通修改

```python
my_dict = {'name': 'isaac'}

# 字典中添加和修改数据，使用key值进行添加和修改
# 字典[key] = 数据值;  如果key值存在就是修改，如果key值不存在，就是添加

my_dict['age'] = 18  # key值不存在，添加
print(my_dict)  # {'name': 'isaac', 'age': 18}

my_dict['age'] = [1, 2, 3]  # key值已经存在，就是修改数据
print(my_dict)  # {'name': 'isaac', 'age': [1, 2, 3]}

# 注意点：key值 int的1 和 float的1.0 代表一个key值 2和2.0一样，3和3.0一样……
my_dict[1] = 'int'
print(my_dict)  # {'name': 'isaac', 'age': [1, 2, 3], 1: 'int'}
my_dict[1.0] = 'float'
print(my_dict)  # {'name': 'isaac', 'age': [1, 2, 3], 1: 'float'}
```

###### <2> dict.update(dict2)

`dict.update(dict2)`把字典参数 `dict2` 的 `key:value`对 更新到字典 `dict` 里。

```python
dic = {'Name': 'Lsgogroup', 'Age': 7}
dic2 = {'Sex': 'female', 'Age': 8}
dic.update(dic2)
print(dic)  
# {'Sex': 'female', 'Age': 8, 'Name': 'Lsgogroup'}
```

##### 字典中删除数据

###### <1> del 字典名[key]

###### <2> 字典.pop(key)

###### <3> 字典.clear()

###### <4> del 字典名

###### <5> 字典.popitem()

```python
my_dict = {'name': 'isaac', 'age': 19, 1: 'float', 2: 'aa'}

# 1.根据key值删除数据  del 字典名[key]
del my_dict[2]
print(my_dict)  # {'name': 'isaac', 'age': [1, 2, 3], 1: 'float'}

# 2.字典.pop(key)  根据key值删除，返回值是删除的key对应的value值
result = my_dict.pop('age')
print(my_dict)  # {'name': 'isaac', 2: 'aa'}
print(result)  # 19

# 3.字典.clear() 清空字典，删除所有的键值对
my_dict.clear()
print(my_dict)  # {}

# 4.del 字典名  直接将这个字典删除，不能使用这个字典了
del my_dict  # 后边的代码不能再直接使用这个变量了，除非再次定义
print(my_dict)  # NameError: name 'my_dict' is not defined

# 5.dict.popitem()随机返回并删除字典中的一对键和值，如果字典已经为空，却调用了此方法，就报出KeyError异常。
dic1 = {1: "a", 2: [1, 2]}
print(dic1.popitem())  # (1, 'a')
print(dic1)  # {2: [1, 2]}
```

##### 字典中遍历数据

###### <1> for循环直接遍历字典，遍历的是字典的key值（自己测试value也可以。。）

```python
my_dict = {'name': 'isaac', 'age': 18, 'gender': '男'}

# for循环体使用key直接遍历字典
for key in my_dict:
    print(key, my_dict[key])
    # name isaac
    # age 18
    # gender 男
    
# for循环体使用value直接遍历字典
for value in my_dict:
    print(value, my_dict[value])
    # name isaac
    # age 18
    # gender 男
```

###### <2> 字典.keys()

```python
my_dict = {'name': 'isaac', 'age': 18, 'gender': '男'}

# 字典.keys() 获取字典中所有的key值，得到的类型是dict_keys，该类型具有的特点是
# 1. 可以使用list() 进行类型转换，即将其转换为列表类型
# 2. 可以使用for循环进行遍历
result = my_dict.keys()
print(result, type(result))  # dict_keys(['name', 'age', 'gender']) <class 'dict_keys'>
for key in result:
    print(key)
    # name
    # age
    # gender
```

###### <3> 字典.values()

```python
my_dict = {'name': 'isaac', 'age': 18, 'gender': '男'}

# 字典.values() 获取所有的value值，类型是 dict_values
# 1. 可以使用list() 进行类型转换，即将其转换为列表类型
# 2. 可以使用for循环进行遍历
result = my_dict.values()
print(result, type(result))  # dict_values(['isaac', 18, '男']) <class 'dict_values'>
for value in my_dict.values():
    print(value)
```

###### <4> 字典.items()

```python
my_dict = {'name': 'isaac', 'age': 18, 'gender': '男'}

# 字典.items()  获取所有的键值对，类型是 dict_items，（key,value)组成元组类型
# 1.可以使用list() 进行类型转换，即将其转换为列表类型
# 2.可以使用for循环进行遍历
result = my_dict.items()  # ()是元组，你还记得吗
print(list(result))  # [('name', 'isaac'), ('age', 18), ('gender', '男')]
print(result, type(result))  # dict_items([('name', 'isaac'), ('age', 18), ('gender', '男')]) <class 'dict_items'>
for item in my_dict.items():
    print(item[0], item[1])
    # name isaac
    # age 18
    # gender 男

# 拆包：将容器中的数据分别给到不同的变量
for k, v in my_dict.items():  # k是元组中的第一个数据，v是元组中的第二个数据
    print(k, v)
    # name isaac
    # age 18
    # gender 男
```

#### 容器的公共方法

##### 1. 运算符

| 运算符 | Python 表达式      | 结果                         | 描述           | 支持的数据类型           |
| :----- | ------------------ | ---------------------------- | -------------- | ------------------------ |
| +      | [1, 2] + [3, 4]    | [1, 2, 3, 4]                 | 合并           | 字符串、列表、元组       |
| *      | ['Hi!'] * 4        | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 复制           | 字符串、列表、元组       |
| in     | 3 in (1, 2, 3)     | True                         | 元素是否存在   | 字符串、列表、元组、字典 |
| not in | 4 not in (1, 2, 3) | True                         | 元素是否不存在 | 字符串、列表、元组、字典 |

###### **注意：**

**+，*得到的是一个新容器**

**in/not in判断的是字典的key值是否存在**



###### +

```python
>>> "hello " + "itcast"
'hello itcast'
>>> [1, 2] + [3, 4]
[1, 2, 3, 4]
>>> ('a', 'b') + ('c', 'd')
('a', 'b', 'c', 'd')
```

###### *

```python
>>> 'ab' * 4
'ababab'
>>> [1, 2] * 4
[1, 2, 1, 2, 1, 2, 1, 2]
>>> ('a', 'b') * 4
('a', 'b', 'a', 'b', 'a', 'b', 'a', 'b')
```

###### in

```python
>>> 'itc' in 'hello itcast'
True
>>> 3 in [1, 2]
False
>>> 4 in (1, 2, 3, 4)
True
>>> "name" in {"name":"Delron", "age":24}
True
```

**注意，in在对字典操作时，判断的是字典的键**

##### 2. python内置函数

Python包含了以下内置函数

| 序号 | 方法      | 描述                 |
| :--- | --------- | -------------------- |
| 1    | len(item) | 计算容器中元素个数   |
| 2    | max(item) | 返回容器中元素最大值 |
| 3    | min(item) | 返回容器中元素最小值 |
| 4    | del(item) | 删除变量             |

###### 注意：

max/min 对于字典来说，比较的是字典的key值得大小

###### len

```python
>>> len("hello itcast")
12
>>> len([1, 2, 3, 4])
4
>>> len((3,4))
2
>>> len({"a":1, "b":2})
2
```

**注意：len在操作字典数据时，返回的是键值对个数。**

###### max

```python
>>> max("hello itcast")
't'
>>> max([1,4,522,3,4])
522
>>> max({"a":1, "b":2})
'b'
>>> max({"a":10, "b":2})
'b'
>>> max({"c":10, "b":2})
'c'
```

###### del

del有两种用法，一种是del加空格，另一种是del()

```python
>>> a = 1
>>> a
1
>>> del a
>>> a
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'a' is not defined
>>> a = ['a', 'b']
>>> del a[0]
>>> a
['b']
>>> del(a)
>>> a
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'a' is not defined
```

##### 3. 多维列表/元祖访问的示例

```python
>>> tuple1 = [(2,3),(4,5)]
>>> tuple1[0]
(2, 3)
>>> tuple1[0][0]
2
>>> tuple1[0][2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: tuple index out of range


>>> tuple1[0][1]
3
>>> tuple1[2][2]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range


>>> tuple2 = tuple1+[(3)]
>>> tuple2
[(2, 3), (4, 5), 3]
>>> tuple2[2]
3
>>> tuple2[2][0]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'int' object is not subscriptable
```





## 练习题

### 1、字典基本操作

字典内容如下:

```python
dic = {
    'python': 95,
    'java': 99,
    'c': 100
    }
```

用程序解答下面的题目

- 字典的长度是多少
- 请修改'java' 这个key对应的value值为98
- 删除 c 这个key
- 增加一个key-value对，key值为 php, value是90
- 获取所有的key值，存储在列表里
- 获取所有的value值，存储在列表里
- 判断 javascript 是否在字典中
- 获得字典里所有value 的和
- 获取字典里最大的value
- 获取字典里最小的value
- 字典 dic1 = {'php': 97}， 将dic1的数据更新到dic中

```python
dic = {
    'python': 95,
    'java': 99,
    'c': 100
}

print(len(dic))

dic['java'] = 98
print(dic)

del dic['c']
print(dic)

dic['php'] = 90
print(dic)

lst1 = list(dic.keys())
print(lst1)

lst2 = list(dic.values())
print(lst2)

print('javascript' in dic)

print(sum(value for value in lst2))

print(max(value for value in lst2))

print(min(value for value in lst2))

dic1 = {'php': 97}
dic.update(dic1)
print(dic)
```

> 3
> {'python': 95, 'java': 98, 'c': 100}
> {'python': 95, 'java': 98}
> {'python': 95, 'java': 98, 'php': 90}
> ['python', 'java', 'php']
> [95, 98, 90]
> False
> 283
> 98
> 90
> {'python': 95, 'java': 98, 'php': 97}

### 2、字典中的value

有一个字典，保存的是学生各个编程语言的成绩，内容如下

```python
data = {
        'python': {'上学期': '90', '下学期': '95'},
        'c++': ['95', '96', '97'],
        'java': [{'月考':'90', '期中考试': '94', '期末考试': '98'}]
        }
```

各门课程的考试成绩存储方式并不相同，有的用字典，有的用列表，但是分数都是字符串类型，请实现函数`transfer_score(score_dict)`，将分数修改成int类型

```python
data = {
    'python': {'上学期': '90', '下学期': '95'},
    'c++': ['95', '96', '97'],
    'java': [{'月考': '90', '期中考试': '94', '期末考试': '98'}]
}


def transfer_score(data):
    for x in data['python']:
        data['python'][x] = eval(data['python'][x])
    for x in range(0, len(data['c++'])):
        data['c++'][x] = eval(data['c++'][x])
    for x in data['java'][0]:
        data['java'][0][x] = eval(data['java'][0][x])


transfer_score(data)
print(data)

```

> {'python': {'上学期': 90, '下学期': 95}, 'c++': [95, 96, 97], 'java': [{'月考': 90, '期中考试': 94, '期末考试': 98}]}

## 集合

## 练习题

**练习题**：

1. 怎么表示只包含⼀个数字1的元组。

   ```python
   tup = (1,)
   print(type(tup))
   ```

   > <class 'tuple'>

2. 创建一个空集合，增加 {‘x’,‘y’,‘z’} 三个元素。

   ```python
   letter = set('xyz')
   print(letter)
   ```

   > {'x', 'y', 'z'}

3. 列表['A', 'B', 'A', 'B']去重。

   ```python
   big_letter = set(['A', 'B', 'A', 'B'])
   print(list(big_letter))
   ```

   > ['A', 'B']

4. 求两个集合{6, 7, 8}，{7, 8, 9}中不重复的元素（差集指的是两个集合交集外的部分）。

   ```python
   set1 = {6, 7, 8}
   set2 = {7, 8, 9}
   print(set1 ^ set2)
   ```

   > {9, 6}

5. 求{'A', 'B', 'C'}中元素在 {'B', 'C', 'D'}中出现的次数。

   ```python
   set1 = {'A', 'B', 'C'}
   set2 = {'B', 'C', 'D'}
   print(len(set1 & set2))
   ```

   > 2

## 序列

## 练习题

1. 怎么找出序列中的最⼤、⼩值？

   max(sub)返回序列或者参数集合中的最大值

   min(sub)返回序列或者参数集合中的最小值

2. sort() 和 sorted() 区别

   sort()直接在原列表中排序，sorted()返回一个排好序新列表

3. 怎么快速求 1 到 100 所有整数相加之和？

   sum(range(101))

4. 求列表 [2,3,4,5] 中每个元素的立方根。

   ```python
   lst = []
   for i in [2, 3, 4, 5]:
       lst.append(i ** 2)
   ```

5. 将[‘x’,‘y’,‘z’] 和 [1,2,3] 转成 [(‘x’,1),(‘y’,2),(‘z’,3)] 的形式。

```python
lst1 = ['x', 'y', 'z']
lst2 = [1, 2, 3]
zipped = zip(lst1,lst2)
print(list(zipped))
```

> [('x', 1), ('y', 2), ('z', 3)]