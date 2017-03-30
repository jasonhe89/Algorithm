```python
def insertAtV(self, head, n):
        while head.val != n:
            head = head.next
        temp = ListNode(10)
        temp.next = head.next
        head.next = temp
```