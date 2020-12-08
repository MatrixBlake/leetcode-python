# 链接
https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/

与leetcode第240题相同 https://leetcode-cn.com/problems/search-a-2d-matrix-ii/

# 题目

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


**示例**：
**输入**：
 <pre>
>\[  
> \[1,   4,  7, 11, 15],  
> \[2,   5,  8, 12, 19],  
> \[3,   6,  9, 16, 22],  
> \[10, 13, 14, 17, 24],  
> \[18, 21, 23, 26, 30]  
>]
 </pre>


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

