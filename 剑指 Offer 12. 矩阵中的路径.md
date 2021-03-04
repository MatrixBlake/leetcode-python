# 链接
https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/

与主站79题相同 https://leetcode-cn.com/problems/word-search/

# 题目
请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中的任意一格开始，每一步可以在矩阵中向左、右、上、下移动一格。如果一条路径经过了矩阵的某一格，那么该路径不能再次进入该格子。例如，在下面的3×4的矩阵中包含一条字符串“bfce”的路径（路径中的字母用加粗标出）。
<pre>
[["a","<b>b</b>","c","e"],
["s","<b>f</b>","<b>c</b>","s"],
["a","d","<b>e</b>","e"]]
</pre>
但矩阵中不包含字符串“abfb”的路径，因为字符串的第一个字符b占据了矩阵中的第一行第二个格子之后，路径不能再次进入这个格子。

**示例1**
<pre>
输入：board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
输出：true
</pre>

**示例2**
<pre>
输入：board = [["a","b"],["c","d"]], word = "abcd"
输出：false
</pre>

# 题解
经典DFS的回溯问题，将每个问题分成四个方向上的子问题，但是要注意使用一个表记录是否已经走过，并记得在回溯时还原。

```python
class Solution:
    def exist(self, board, word) -> bool:
        def dfs(i,j,k):
            if i<0 or i>=len(board) or j<0 or j>=len(board[0]) or visited[i][j] or board[i][j]!=word[k]:
                return False
            if k == len(word)-1:
                return True
            visited[i][j] = True
            res = dfs(i-1,j,k+1) or dfs(i+1,j,k+1) or dfs(i,j-1,k+1) or dfs(i,j+1,k+1)
            visited[i][j] = False
            return res

        for i in range(len(board)):
            for j in range(len(board[0])):
                visited=[]
                for m in range(len(board)):
                    visited.append([False]*len(board[0]))
                if dfs(i,j,0):
                    return True
        return False
'''
