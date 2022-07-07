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

# sorted用法
## dictionary定义sort的key
```python
sorted_dict = sorted(dict_exmaple.items(), key=lambda x: x[1], reverse=True)
s = sorted(word_count.items(), key= lambda x:(-x[1],x[0]))
```
## 自定义compare函数
```python
def compare(x, y):
    a, b = x + y, y + x
    if a > b: return 1
    elif a < b: return -1
    else: return 0
res = sorted(nums,key = functools.cmp_to_key(compare))
```

# 位运算trick
对于整数 val 二进制的第 i 位，我们可以用代码 (val >> i) & 1 来取出其第 i 位的值

# 滑动窗口
```python
l = 0
res = 0
temp = 0
for r, num in enumerate(nums):
    更新temp
    while l <= r and 需要的条件:
        更新temp
        l += 1 #左端收缩
    res += l - r + 1
```

# 二分问题
## unique数组找target
```python
# [1,2,3,4] 找3
l,r = 0, len(nums)
while l<=r:
    mid = (l+r)//2
    if nums[mid] < target:
        l = mid + 1
    elif nums[mid] > target:
        r = mid - 1
    else:
        return mid
return -1
```

## 找第一个等于target的index  
```python
# [1,2,3,3,3,4] 找第一个3
l,r = 0, len(nums)
while l<=r:
    mid = (l+r)//2
    if nums[mid] < target: #只要小于，就可以把左端往右移
        l = mid + 1
    else:
        r = mid - 1
if nums[l] == target:
    return l
return -1
```

## 找第最后一个等于target的index  
```python
# [1,2,3,3,3,4] 找最后一个3
l,r = 0, len(nums)
while l<=r:
    mid = (l+r)//2
    if nums[mid] <= target: #只要小于或者等于，就可以把左端往右移，一直移到比target值还大或者l越界（也就是target是最后一个值）
        l = mid + 1
    else:
        r = mid - 1
if nums[l] == target:
    return l-1
return -1
```


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

## SortedList
```python
from sortedcontainers import SortedList
lst = SortedList()
lst.add((-score, name))

print(lst[n][1]) #返回第n个最大值


from sortedcontainers import SortedList
lst = SortedList()
lst.add(num) #logn
ind = bisect_left(lst,num) #找num的index,logn
lst.remove(num) #logn

```

## SortedDict
```python
from sortedcontainers import SortedDict
booked = SortedDict()
i = booked.bisect_left(end)
booked[start] = end #以key为sort
```

# 排列组合
```python
comb(m,n)
```

# a-z
```python
string.ascii_lowercase
```
