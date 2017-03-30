```
        n6-----------n5
        |            |
  n1--- n2---n3--- n4|

```

我们仍然可以使用两个指针fast和slow，fast走两步，slow走一步，判断是否有环，当有环重合之后，譬如上面在n5重合了，那么如何得到n2呢？

首先我们知道，fast每次比slow多走一步，所以重合的时候，fast移动的距离是slot的两倍，我们假设n1到n2距离为a，n2到n5距离为b，n5到n2距离为c，fast走动距离为`a + b + c + b`，而slow为`a + b`，有方程`a + b + c + b = 2 x (a + b)`，可以知道`a = c`，所以我们只需要在重合之后，一个指针从n1，而另一个指针从n5，都每次走一步，那么就可以在n2重合了。

```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None

#确定链表中是否有cycle
def cycle(node):
    slow = node
    fast = node
    #
    while fast.next and fast.next.next != None:
        fast = fast.next.next
        slow = slow.next
        if fast == slow:
            break
    
    return fast
#找到cycle中的开头
def findCycleStart(node):
    slow = node
    fast = node
    
    while fast.next and fast.next.next != None:
        fast = fast.next.next
        slow= slow.next
        if fast == slow:
            break
    slow = node
    while slow != fast:
        slow = slow.next
        fast = fast.next
    return slow
        
    
a = Node(1)
b = Node(2)
c = Node(3)
f = Node(4)
e = Node(5)

a.next = b
b.next = c
c.next = f
f.next = e
e.next = c
cycle(a).val
findCycleStart(a).val
```