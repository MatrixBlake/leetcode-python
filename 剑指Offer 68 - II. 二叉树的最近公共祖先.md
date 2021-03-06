# 链接
https://leetcode-cn.com/problems/er-cha-shu-de-zui-jin-gong-gong-zu-xian-lcof/

# 题目
给定一个二叉树, 找到该树中两个指定节点的最近公共祖先。

百度百科中最近公共祖先的定义为：“对于有根树 T 的两个结点 p、q，最近公共祖先表示为一个结点 x，满足 x 是 p、q 的祖先且 x 的深度尽可能大（一个节点也可以是它自己的祖先）。”

例如，给定如下二叉树:  root = [3,5,1,6,2,0,8,null,null,7,4]

![image](https://user-images.githubusercontent.com/30548164/112714928-fcf44080-8f30-11eb-8fad-f31d346bcaa7.png)

**示例1**：
<pre>
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
输出: 3
解释: 节点 5 和节点 1 的最近公共祖先是节点 3。
</pre>


**示例2**：
<pre>
输入: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
输出: 5
解释: 节点 5 和节点 4 的最近公共祖先是节点 5。因为根据定义最近公共祖先节点可以为节点本身。
</pre>

# 题解
**思路**：
- 当一个节点是最近共组祖先的时候，一定满足以下性质之一：(1)p和q是一个在自己的左节点里一个在自己的右节点里; (2)p是该节点，q是在它的子节点里; (3) q是该节点，p在它的子节点里
- 二叉树的搜索通常可以使用DFS
- 因为这题是返回节点，所以dfs返回的一般来说应该是节点
- DFS终止的条件一般为找到了终点或者找到了要的，那么在这个问题里就可以设计成，找到为空或者找到了和p或者q相等的节点。
- 每次都dfs左节点和右节点
- 如果返回的两个结果都是有的，在(1)的情况下说明这个节点就是我们要的（因为如果两个有一个为空，说明结果应该在某一个子树里）。如果其中一个是空的，那么另一个的返回结果就是我们要的（同时也考虑了(2)(3)的情况）

```python
class Solution:
    def lowestCommonAncestor(self, root: TreeNode, p: TreeNode, q: TreeNode) -> TreeNode:
        if not root or root == p or root == q: return root
        left = self.lowestCommonAncestor(root.left, p, q)
        right = self.lowestCommonAncestor(root.right, p, q)
        if not left: return right
        if not right: return left
        return root
```
