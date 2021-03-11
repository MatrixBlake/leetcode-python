# 链接
https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/

# 题目
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

**示例**：
<pre>
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
</pre>

# 题解
**思路**：
- 1 -> 2 -> 3
- 更改每一个next的指向，注意得先把后一个节点先存下来，否则改完1和2的指向我们会找不到3
```python
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        pre = None
        cur = head
        while cur:
            nex = cur.next
            cur.next = pre
            pre = cur
            cur = nex
        return pre
```
