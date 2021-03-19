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
- while条件：left <= right 
- mid = (left+right)//2
- left = mid +1
- right = mid - 1


## 解法二：线性查找
**思路**：从左下角起，和target比大小，大就上移，小就右移（因为两个方向上的信息不一样）。当然也可以从右上角起算。

**复杂度**：时间复杂度O(n+m)

```python
class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        n = len(matrix)
        try:
            m = len(matrix[0])
        except:
            return False
        if n == 0:
            return False

        i = n -1
        j = 0
        while i>=0 and j<m:
            if matrix[i][j] < target:
                j += 1
            elif matrix[i][j] > target:
                i -= 1
            else:
                return True
        return False
```

# 启发
遇到二维数组，可以把四个角的性质都想想。
