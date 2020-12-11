# 链接
https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/


# 题目

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )


**示例**：

<pre>
<b>输入</b>：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
<b>输出</b>：[null,null,3,-1]
</pre>

<pre>
<b>输入</b>：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
<b>输出</b>：[null,-1,null,null,5,2]
</pre>


# 题解
**思路**：栈stack，先进后出(FILO)，只能在尾部进行append和pop操作，所以使用删除头部操作的时候，需要以此把尾部pop出来，append进一个新的stack。



```python
class CQueue:

    def __init__(self):
        self.stack1 = []
        self.stack2 = []


    def appendTail(self, value: int) -> None:
        self.stack1.append(value)

    def deleteHead(self) -> int:
        if self.stack2: 
            return self.stack2.pop()
        if self.stack1:
            while self.stack1:
                self.stack2.append(self.stack1.pop(-1))
            return self.stack2.pop(-1) 
        else:
            return -1

```

# 启发
题目很简单，记清楚stack和queue的性质就好。
