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
## 解法一：dictionary
**思路**：遍历数组，把值存到一个dictionary里面，如果已经存在了，那就返回。

**缺陷**：没有使用到 0~n-1这个information。

**复杂度**：时间复杂度O(N), 空间复杂度O(N)

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
## 解法二：类似于自然数组排序
**思路**：遍历index，当处于0位置的时候，如果上面不是0，则进行一系列交换操作，假设上面的数字是4，就将这个4和位置4上的数(比如2)交换，再去把这个2和位置上的数(比如0)交换，这个时候0在位置0上了，我们就move到下一个index。因为最多只需要交换N次，额外不需要交换的判断最多N次，所以是O(N)的时间复杂度，没有使用额外空间，所以是O(1)的空间复杂度。

**复杂度**：时间复杂度O(N), 空间复杂度O(1)

**例子**：
| i | 现在的list |
--- | --- 
| i = 0 | [3, 2, 0 ,1 ,1] |
| i = 0 | [1, 2, 0 ,3 ,1] |
| i = 0 | [2, 1, 0 ,3 ,1] |
| i = 0 | [0, 1, 2 ,3 ,1] |
| i = 1 | [0, 1, 2 ,3 ,1] |
| i = 2 | [0, 1, 2 ,3 ,1] |
| i = 3 | [0, 1, 2 ,3 ,1] |
| i = 4 | [0, 1, 2 ,3 ,1] |

此时发现，需要交换的数字相等了，所以返回1。

```python
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            while i != nums[i]:
                if nums[i] == nums[nums[i]]:
                    return nums[i]
                else:
                    temp = nums[nums[i]]
                    nums[nums[i]] = nums[i]
                    nums[i] = temp
        return -1
```
**注意点**：
- 判断是while，也就是说每个index上可能会做多次交换
- 交换的时候，不能写nums[i] = nums[nums[i]], 而是要写nums[nums[i]] = nums[i]

