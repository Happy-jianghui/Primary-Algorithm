# 链表
## 237.删除链表中的节点
**解题思路**：原节点的下一个节点的值赋值给原节点，然后改变原节点的指针，指向到下下一个节点。
```Python
def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
```

## 19.删除链表的倒数第N个节点
**解题思路**：快慢指针，设置虚拟节点 dummy 指向 head设定双指针 p 和 q，初始都指向虚拟节点 dummy，移动q，直到p与q之间相隔的元素个数为n，同时移动p与q，直到q指向的为 NULL，将p的下一个节点指向下下个节点
```Python
def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
```

## 206.反转链表
**解题思路**：遍历链表，并在访问各节点时修改 next 引用指向
```Python
def reverseList(self, head: ListNode) -> ListNode:
        cur, pre = None, head
        while pre:
            temp = pre.next
            pre.next = cur
            cur = pre
            pre = temp
        return cur
```
