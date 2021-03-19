# 链接
https://leetcode-cn.com/problems/chou-shu-lcof/

# 题目
我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

**示例**：
<pre>
输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
</pre>

# 题解
**思路**：
- 指针 + DP
- 每个指针对应着现在需要乘2，3，5的值，然后三个candidate取选最小的那个，选了以后对应的指针就往后走一步
- 注意 2X3 和 3X2 都会得到6，所以都得往前走一步，因为下次不会想要6了。

```python
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        p_list = [0, 0, 0]
        dp = [1]*n
        
        for i in range(1,n):           
            cand_list = [dp[p_list[0]]*2, dp[p_list[1]]*3, dp[p_list[2]]*5]
            small_value = min(cand_list)
            dp[i] = small_value
            for ind in range(3):
                if cand_list[ind] == small_value:
                    p_list[ind] += 1

        return dp[-1]
```
