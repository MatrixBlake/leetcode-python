# 链接
https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/

# 题目
输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。

**示例**：
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.

# 题解
**思路**：
- 链表就用指针。
- 这题可以用双指针，巧妙的先把K个位置空出来，然后大家一起往后走。
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getKthFromEnd(self, head: ListNode, k: int) -> ListNode:
        pre = head
        cur = head
        for i in range(k):
            cur = cur.next
        while cur:
            pre = pre.next
            cur = cur.next
        return pre
```
