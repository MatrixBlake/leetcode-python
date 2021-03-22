# 链接
https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/

# 题目
给定一棵二叉搜索树，请找出其中第k大的节点。

**示例**：
<pre>
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
</pre>

# 题解
**思路**：搜索二叉树的性质——二叉搜索树的中序遍历为 递增序列 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def kthLargest(self, root: TreeNode, k: int) -> int:
        def dfs(root):
            return dfs(root.left) + [root.val] + dfs(root.right) if root else []
        return dfs(root)[-k]
```
