# TASK9

## 文件

文件的作用：可以永久的保存数据。

文件在硬盘中存储的格式是二进制。

1.打开文件

2.读写文件

3.关闭文件

### 读文件-r

```python
# 1.打开文件，是文件从硬盘中存到内存中
# open(file, mode='r', encoding)
# file 要操作的文件名字，类型为字符串
# mode，文件打开的方式，r(read)只读打开，w(write)只写打开，a(append) 追加打开
# encoding 文件的编码格式，常见的有两种，一种是gbk，一种是utf-8
# 返回值 是文件对象，后续所有的文件操作，都需要通过这个文件对象进行
# read以只读的方式打开当前目录中，1.txt 文件,文件不存在会报错
f = open('1.txt', 'r')
# 2.读文件 文件对象.read()
buf = f.read()
print(buf)
# 3.关闭文件  文件.close() 将内存中的三大文件同步到硬盘中
f.close()
```

### 写文件-w

```python
# 1.打开文件 w 方式打开文件:文件不存在，会创建文件；文件存在，会覆盖清空原文件
f = open('a.txt', 'w')
# 2.写文件 文件对象.write(写入文件的内容)
f.write('hello world!\n')
f.write('hello python\n')
f.write('你好，中国！')
# 3.关闭文件
f.close()
```

![image-20210201213137490](TASK9.assets/image-20210201213137490.png)

```python
# 1.打开文件 w 方式打开文件:文件不存在，会创建文件；文件存在，会覆盖清空原文件
f = open('a.txt', 'w', encoding='utf-8')
# 2.写文件 文件对象.write(写入文件的内容)
f.write('hello world!\n')
f.write('hello python\n')
f.write('你好，中国！')
# 3.关闭文件
f.close()
```

### 追加文件-a

**注意点**：不管是 a 方式打开文件，还是 w 方式打开文件，写内容，都是使用 write()函数

```python
# a 方式打开文件，追加内容，在文件的末尾写入内容
# 文件不存在，会创建文件
# 注意点：不管是 a 方式打开文件，还是 w 方式打开文件，写内容，都是使用 write()函数，不能读，只能写
f = open('b.txt', 'a', encoding='utf-8')
f.write('hello world\n')
f.write('111')
f.close()
```

### 文件读操作

一次打开的文件，内容只能读取一次，因为读过的内容光标后移了，前面的内容就不会再读了

#### read()

```python
# 1.打开文件
f = open('a.txt','r',encoding='utf-8')
# 2.读写文件 文件对象.read(n) 指一次读取n个字节的内容，默认不写则读取所有内容
buf = f.read(3)
print(buf)  # 123
buf = f.read(3)
print(buf)  # 此时读取的是4\n5 ,显示出来的是4
#                                       5
# 3.关闭文件
f.close()
```

![image-20210204155833159](TASK9.assets/image-20210204155833159.png)

#### 按行读取

```python
f = open('a.txt', 'r', encoding='utf-8')
# f.readline()  # 一次读取一行的内容，返回值是读到的内容（str）
# buf = f.readline()
# print(buf)

# f.readlines()  # 按行读取，一次读取所有行，返回值是列表，列表中的每一项是一个字符串，即一行的内容
buf = f.readlines()
print(buf)
# ['1234\n', '5678\n']
buf = [i.strip() for i in buf]  # 去除换行符\n
print(buf)
# ['1234', '5678']
f.close()
```

### 模拟拷贝大文件

```python
read()  一次读取全部的内容
read()/readline()  读到文件末尾会返回空
```

![](TASK9.assets/image-20210204164741614.png)

![](TASK9.assets/image-20210203165930441.png)

### 文件打开模式

```python
文本文件：txt .py  .md 能够使用记事本打开的文件
二进制文件：具有特殊格式的文件，mp3 mp4 rmvb avi png jpg等

文本文件可以使用 文本方式打开文件，也可以使用二进制的方式打开文件

二进制文件，只能使用二进制的方式打开文件
二进制打开方式如下：不管读取，还是书写，都需要使用二进制的数据
rb wb ab
注意点：不能指定 encoding 参数
```

![image-20210204165552812](TASK9.assets/image-20210204165552812.png)

![image-20210204165930857](TASK9.assets/image-20210204165930857.png)

| 访问模式 | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| r        | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
| w        | 打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。 |
| a        | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| rb       | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。 |
| wb       | 以二进制格式打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。 |
| ab       | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| r+       | 打开一个文件用于读写。文件指针将会放在文件的开头。           |
| w+       | 打开一个文件用于读写。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。 |
| a+       | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。 |
| rb+      | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。 |
| wb+      | 以二进制格式打开一个文件用于读写。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。 |
| ab+      | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。 |

### 文件备份

```python
1.用只读的方式，打开文件
2.读取文件内容
3.关闭文件
4.只写的方式打开新文件
5.将第 2 步读取的内容写入新文件
6.关闭新文件

代码优化：
	1.如果文件比较大，循环读取文件
	2.复制备份的文件可能是txt文件，可能是二进制文件 ---> 使用二进制方式打开文件
```

![image-20210204194419415](TASK9.assets/image-20210204194419415.png)

```python
file_name = input("请输入要备份的文件名")

# 1.用只读的方式打开文件
f = open(file_name, 'rb')
# 2.读取文件内容
buf = f.read()
# 3.关闭文件
f.close()

# 根据原文件名，找到文件后缀和文件名
index = file_name.rfind('.')
# 后缀 file_name[index: ]
# 新文件名
new_file_name = file_name[:index]+'[备份]'+file_name[index:]

# 4.只写的方式打开新文件
f_w = open(new_file_name, 'wb')
# 5.将 第2步 读取的内容写入新文件
f_w.write(buf)
# 6.关闭新文件
f_w.close()
```

### 文件和文件夹的相关操作

有些时候，需要对文件进行重命名、删除等一些操作，python的os模块中都有这么功能

#### 1. 文件重命名

os模块中的rename()可以完成对文件的重命名操作

rename(需要修改的文件名, 新的文件名)

```python
import os
os.rename("毕业论文.txt", "毕业论文-最终版.txt")
```

#### 2. 删除文件

os模块中的remove()可以完成对文件的删除操作

remove(待删除的文件名)

```python
import os
os.remove("毕业论文.txt")
```

#### 3. 创建文件夹

```python
import os
os.mkdir("张三")
```

#### 4. 获取当前目录

```python
import os
os.getcwd()
```

#### 5. 改变默认目录

```python
import os
os.chdir("../")
```

#### 6. 获取目录列表

```python
import os
os.listdir("./")
```

#### 7. 删除文件夹

```python
import os
os.rmdir("张三")
```

#### 实操：

```python
# 对文件和目录的操作，需要导入os模块
import os

# 1.文件重命名 os.rename(原文件路径名，新文件路径名)
# os.rename('a.txt','aa.txt')

# 2.删除文件 os.remove(文件的路径名)
# os.remove('aa.txt')

# 3.创建目录 os.mkdir(目录路径名)  make directory
# os.mkdir('test')
# os.mkdir('test/aa')

# 4.删除空目录 os.rmdir(目录名)  remove directory
# os.rmdir('test/aa')

# 5.获取当前所在的目录 os.getcwd()  get current working directory
buf = os.getcwd()
print(buf)

# 6.修改当前的目录 os.chdir(目录名)  change directory 只是切换了代码正在操作的文件目录，没有移动文件
os.chdir('test')
buf = os.getcwd()
print(buf)

# 7.获取指定目录中的内容 os.listdir(目录)，默认不写参数，是获取当前目录中的内容
# 返回值是列表，列表中的每一项是文件名
buf = os.listdir()  # test
print(buf)
```

### 批量修改文件名

`../`指上级目录

```python
import os


def create_files_0():
    for i in range(10):
        file_name = "test/file_" + str(i) + '.txt'
        f = open(file_name, 'w')
        f.close()


def create_files_1():
    os.chdir('test')
    for i in range(10, 20):
        file_name = "file_" + str(i) + '.txt'
        f = open(file_name, 'w')
        f.close()
    os.chdir('../')  # ../ 上一级目录


def modify_filename_0():
    os.chdir('test')
    buf_list = os.listdir()
    # print(buf_list)
    for file in buf_list:
        new_file = 'py43_' + file
        os.rename(file, new_file)
        
    os.chdir('../')


def modify_filename_1():
    os.chdir('test')
    buf_list = os.listdir()
    # print(buf_list)
    for file in buf_list:
        num = len('py43_')
        new_file = file[num:]
        os.rename(file, new_file)

    os.chdir('../')


create_files_0()
create_files_1()
modify_filename_0()
modify_filename_1()
```

### 

## **练习题**：

1、打开中文字符的文档时，会出现乱码，Python自带的打开文件是否可以指定文字编码？还是只能用相关函数？

可以指定文字编码，open(xxx,encoding='utf-8'/'gbk',xxx)

2、编写程序查找最长的单词

输入文档: res/test.txt

题目说明:

```python
def longest_word(filename):
    f = open(filename, 'r', encoding='utf-8')
    word_list = []
    word = ''
    for j in f.read():
        for i in j:
            if i == ',':
                word_list.append(word)
                word = ''
            else:
                word += i
    word_list = [i.strip() for i in word_list]
    max_len = max(len(word) for word in word_list)
    longest_word_list = [word for word in word_list if len(word) == max_len]
    print(longest_word_list)
    f.close()


file_name = input('请输入要查找最长单词的文档：')
longest_word(file_name)

```
