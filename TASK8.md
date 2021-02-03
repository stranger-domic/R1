# TASK8

## 模块

### **练习题**：

1、怎么查出通过 from xx import xx导⼊的可以直接调⽤的⽅法？

我没咋懂是啥意思。。这不是这句话从from打到import后面那个空格的时候，就会自动跳出来可以导入的方法列表嘛？

2、了解Collection模块，编写程序以查询给定列表中最常见的元素。

题目说明：

输入：language = ['PHP', 'PHP', 'Python', 'PHP', 'Python', 'JS', 'Python', 'Python','PHP', 'Python']

输出：Python

```python
import collections

language = ['PHP', 'PHP', 'Python', 'PHP', 'Python', 'JS', 'Python', 'Python', 'PHP', 'Python']


def most_element(self):
    count_dict = dict(collections.Counter(self))
    max_value = max(count_dict.values())
    for k, v in count_dict.items():
        if max_value == v:
            print(k)


most_element(language)

```

> Python

## datetime模块

### **练习题**：

1、假设你获取了用户输入的日期和时间如`2020-1-21 9:01:30`，以及一个时区信息如`UTC+5:00`，均是`str`，请编写一个函数将其转换为timestamp：

题目说明:

```python
"""
   
Input file
example1: dt_str='2020-6-1 08:10:30', tz_str='UTC+7:00'
example2: dt_str='2020-5-31 16:10:30', tz_str='UTC-09:00'
   
Output file
result1: 1590973830.0
result2: 1590973830.0
"""
   
   
import re
from datetime import datetime, timezone, timedelta


def to_timestamp(dt_str, tz_str):
    # 首先，获取用户输入的时间的datetime
    input_dt = datetime.strptime(dt_str, '%Y-%m-%d %H:%M:%S')
    # 上面得到的datetime是没有时区的，因此设置用户输入的对应时区
    # 那么此时需要利用正则获取用户输入的时区
    time_zone_num = re.match(r'UTC([+|-][\d]{1,2}):00', tz_str).group(1)
    time_zone = timezone(timedelta(hours=int(time_zone_num)))
    input_dt_tz = input_dt.replace(tzinfo=time_zone)
    return input_dt_tz.timestamp()


t1 = to_timestamp('2020-6-1 08:10:30', 'UTC+7:00')
print(t1)
t2 = to_timestamp('2020-5-31 16:10:30', 'UTC-09:00')
print(t2)

```

2、编写Python程序以选择指定年份的所有星期日。

题目说明:

```python
"""
   
Input file
   2020
   
Output file
   2020-01-05                         
   2020-01-12              
   2020-01-19                
   2020-01-26               
   2020-02-02     
   -----
   2020-12-06               
   2020-12-13                
   2020-12-20                
   2020-12-27 
"""
   
import datetime


def all_sundays(year_name):
    year = int(year_name)
    dt1 = datetime.date(year, 1, 1)
    dt2 = datetime.date(year, 12, 31)
    all_days = (dt2 - dt1).days
    for i in range(all_days + 1):
        day_name = dt1 + datetime.timedelta(days=i)
        weekday = day_name.isoweekday()
        if weekday == 7:
            print(day_name)
        else:
            continue


all_sundays(input('请输入年份:'))

    
```