# 链接
https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/

与leetcode第240题相同 https://leetcode-cn.com/problems/search-a-2d-matrix-ii/

# 题目

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


**示例**：
**输入**：  
>\[  
> \[1,  4,  7, 11, 15],  
> \[2,   5,  8, 12, 19],  
> \[3,   6,  9, 16, 22],  
> \[10, 13, 14, 17, 24],  
> \[18, 21, 23, 26, 30]  
>]


**输出**：2 或 3 

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

