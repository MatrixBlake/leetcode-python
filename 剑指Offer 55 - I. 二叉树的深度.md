# 链接
https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/

# 题目
输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度。

# 题解 DFS
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        def dfs(root):
            if not root:
                return 0
            else:
                return max(dfs(root.left),dfs(root.right))+1
        return dfs(root)
```
