# 链接
https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/

# 题目
给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。要求复杂度：O(N)

**示例**：
<pre>
输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 

  滑动窗口的位置                最大值
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
</pre>

# 题解
**思路**：
- 要O(N)，又是肯定要扫描一遍，所以也就是每个新数字来的时候，不能全看的去比较。
- 一开始的思路是，记录最大值，但是如果最大值刚好被window划走了，就得跟次大值比，那下一次就次大值便最大值还得有次大值。
- 于是想到，维护某个东西，用来保留这个值的大小关系的信息。
- 这题使用了单调递减的list，每次新来一个数字，都把比这个数字小的所有值给pop出去，然后把新的值append在后面，那么每个时刻这个栈的第一个值就是这个时刻的最大值。
- 当然要考虑到滑动窗口的时候删掉的值是不是最大值，所以得判断一下要不要删掉这个list的头。
- 因为每次新元素的比较操作必定带来一次元素的入list或者出list，所以比较操作的总数一定是O(2N)级别的。

```python
class Solution:
    def maxSlidingWindow(self, nums, k):
        if len(nums) == 0:
            return []
        if k == 1:
            return nums
        l = 0
        r = 1
        queue = [nums[0]]
        while r - l < k:
            while queue and nums[r]>queue[-1]:
                queue.pop()
            queue.append(nums[r])
            r += 1
        res = [queue[0]]
        r -= 1

        while r<len(nums)-1:
            deteled = nums[l]
            if queue[0] == deteled:
                queue.pop(0)
            l +=1
            r +=1

            while queue and nums[r]>queue[-1]:
                queue.pop()
            queue.append(nums[r])
            res.append(queue[0])
        return res
```
