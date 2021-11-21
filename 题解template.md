# 回溯
```python
def backtrack("原始参数") {
    //终止条件(递归必须要有终止条件)
    if ("终止条件"):
        //一些逻辑操作（可有可无，视情况而定）
        return

    for i in range("for循环开始的参数", "for循环结束的参数"):
        //一些逻辑操作（可有可无，视情况而定）

        //做出选择

        //递归
        backtrack("新的参数")
        //一些逻辑操作（可有可无，视情况而定）

        //撤销选择
   return
```
# 背包问题

# dictionary以value sort
sorted_dict = sorted(dict_exmaple.items(), key=lambda x: x[1], reverse=True)

s = sorted(word_count.items(), key= lambda x:(-x[1],x[0]))


# 位运算trick
对于整数 val 二进制的第 i 位，我们可以用代码 (val >> i) & 1 来取出其第 i 位的值

# 双指针
## 滑动窗口
两个指针都是从左往右扫描，右边扩大左边收缩
```python
l,r = 0, (0 or 1)
res = total = 0

for r in range(len(nums)):
   更新total值
   while 窗口内数据不满足要求
      1. 更新total值
      2. 收缩左边界
   更新res
返回 res
```

# 二分法
- 定义left和right
- while条件：left <= right
- mid = (left+right)//2
- left = mid +1
- right = mid - 1
- 返回 left

# default dict
```python
from collections import defaultdict

dict1 = defaultdict(int)
dict2 = defaultdict(set)
dict3 = defaultdict(str)
dict4 = defaultdict(list)
```

# 优先队列
## 小顶堆
```python
pq = []
heappush(pq, 3)
v = heappop(pq)
```
## 大顶堆
push进负的值，pop出来的时候再取反

