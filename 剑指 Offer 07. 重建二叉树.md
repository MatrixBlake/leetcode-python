# 链接
https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/

# 题目
输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

**示例**

给出
<pre>
前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
</pre>
返回如下二叉树
<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>

# 题解
## 方法一：递归(divide and conquer)
**思路**：

前序遍历性质： 节点按照 [ 根节点 | 左子树 | 右子树 ] 排序。

中序遍历性质： 节点按照 [ 左子树 | 根节点 | 右子树 ] 排序。

所以用前序的第0个节点，可以从中序找到index，然后分成左子树和右子树两个问题。停止条件，如果是空，返回None。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if len(preorder) == 0:
            return None
        root = preorder[0]
        ind = inorder.index(root)
        tree = TreeNode(root)
        tree.left = self.buildTree(preorder[1:1+ind],inorder[:ind])
        tree.right = self.buildTree(preorder[1+ind:],inorder[1+ind:])
        return tree
```
