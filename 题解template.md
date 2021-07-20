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
对于整数 \textit{val}val 二进制的第 ii 位，我们可以用代码 (val >> i) & 1 来取出其第 ii 位的值

# 滑动窗口
```python
left,right = 0, (0 or 1)
ret = total = 0
while right < len(nums):
   更新total值
   while 窗口内数据不满足要求
      1. 更新total值
      2. 收缩左边界
   更新ret最大值
返回 ret
```
