# 链接
https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/

# 题目
给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

返回删除后的链表的头节点。

**示例1**：
<pre>
输入: head = [4,5,1,9], val = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.
</pre>

**示例2**：
<pre>
输入: head = [4,5,1,9], val = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.
</pre>

# 题解
**思路**：
- 链表要用指针做
- 删除节点的操作是pre.next = cur.next
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def deleteNode(self, head: ListNode, val: int) -> ListNode:
        if head.val == val:
            return head.next
        pre = head
        cur = head.next
        while cur:
            if cur.val == val:
                pre.next = cur.next
                break
            else:
                pre = pre.next
                cur = cur.next
        return head
```

