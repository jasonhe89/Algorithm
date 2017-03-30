\# Definition for singly-linked list with a random pointer.

\# class RandomListNode:

\# def \_\_init\_\_(self, x):

\# self.label = x

\# self.next = None

\# self.random = None

```python
class RandomListNode:
    def __init__(self, x):
        self.label = x
        self.next = None
        self.random = None
def copyRandomList(self, head):
        myMap = {}
        p = head
        dummy = ListNode(0)
        cur = dummy
        while p != None:
            if p in myMap:
                newNode = myMap[p]
            else:
                newNode = RandomListNode(p.val)
            cur.next = newNode

            if p.random != None:
                if p.random in myMap:
                    newNode.random = myMap[p.random]
                else:
                    newNode.random = RandomListNode(p.random.val)
            cur = newNode;
            p = p.next

        return dummy.next
```