# 链接
https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/


# 题目

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )


**示例**：

<pre>
<b>输入<\b>：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
<b>输出<\b>：[null,null,3,-1]
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
