# 链接
https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/

# 题目
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

**示例**：
<pre>
输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2
</pre>

# 题解
**思路**：摩尔投票法
- 核心就是对拼消耗。
- 玩一个诸侯争霸的游戏，假设你方人口超过总人口一半以上，并且能保证每个人口出去干仗都能一对一同归于尽。最后还有人活下来的国家就是胜利。
- 那就大混战呗，最差所有人都联合起来对付你（对应你每次选择作为计数器的数都是众数），或者其他国家也会相互攻击（会选择其他数作为计数器的数），但是只要你们不要内斗，最后肯定你赢。最后能剩下的必定是自己人。
- 时间复杂度O(N)，空间复杂度O(1)

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        s = 0
        for n in nums:
            if s == 0:
                p = n
                s = 1
            else:
                if n == p:
                    s += 1 
                else:
                    s -= 1
        return p
```
