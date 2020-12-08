# 链接
https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/

与leetcode第240题相同 https://leetcode-cn.com/problems/search-a-2d-matrix-ii/

# 题目

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。


**示例**：

给定矩阵如下：
<pre>
[  
[1,   4,  7, 11, 15],  
[2,   5,  8, 12, 19],  
[3,   6,  9, 16, 22],  
[10, 13, 14, 17, 24],  
[18, 21, 23, 26, 30]  
]
</pre>

**输出**：target = 5， 返回 True, target = 20, 返回false

# 题解
## 解法一：二分法
**思路**：对每一行进行二分

**缺陷**：没有使用到每一列从上到下递增的information。

**复杂度**：时间复杂度O(nlog(m))

```python
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        
        n = len(matrix)
        if n == 0:
            return False
        m = len(matrix[0])
        if m == 0:
            return False

        for i in range(n):
            temp_list = matrix[i]
            left = 0
            right = m-1
            while left <= right :
                mid = (left+right)//2
                if temp_list[mid] < target:
                    left = mid + 1                    
                elif temp_list[mid] > target:
                    right = mid - 1
                else:
                    return True
        return False
```
**注意点**：

二分法的步骤：
- 定义left和right
- while条件：left <= right (right = l -1), left < right (right = l)
- mid = (left+right)//2
- left = mid +1
- right = mid - 1 (right = l -1), right = mid (right = l)

