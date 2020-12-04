# 链接
https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/

# 题目

找出数组中重复的数字。

在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**示例**：
>**输入**：  
>[2, 3, 1, 0, 2, 5, 3]  
>**输出**：2 或 3 

# 题解
## 题解一：dictionary
**思路**：遍历数组，把值存到一个dictionary里面，如果已经存在了，那就返回。

**缺陷**：没有使用到 0~n-1这个information。

**复杂度**：时间O(N), 空间O(N)

```python
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        num_dict = {}
        for num in nums:
            if num not in num_dict:
                num_dict[num] = 1
            else:
                return num
        return -1
```
