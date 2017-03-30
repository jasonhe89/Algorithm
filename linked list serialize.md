```python
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
class LinkedList:
    def __init(self):
        self.head = None

    def deserializeList(self,s):
        l = s.split('->')
        nodes = map(lambda x : ListNode(x), l)
        dummy = ListNode(-100)
        dummy.next = nodes[0]
        for i in range(len(nodes) - 1):
            nodes[i].next = nodes[i+1]
        self.head  = dummy.next

def printList(head):
    cur = head
    while cur != None:
        print cur.val
        cur = cur.next
            
def removeElements(head, val):

    # Write your code here
    if head is None:
        return 
    dummy = ListNode(-100)
    dummy.next = head
    pre = dummy
    while head:
        if head.val == val:
            print "find val = " + str(val)
            pre.next = head.next
            head = pre
        pre = head
        head= head.next
    return dummy.next
    
def removeElements(self, head, val):
    # Write your code here
    if head == None:
        return head
    dummy = ListNode(0)
    dummy.next = head
    pre = dummy
    while head:
        if head.val == val:
            pre.next = head.next
            head = pre
        pre = head
        head = head.next
    return dummy.next 


L = LinkedList()
L.deserializeList('1->2->3->3->4->5->3')
#L.printList()
NL = removeElements(L.head, 3)
printList(NL)
#L.printList()
```

[http://www.pythontutor.com/visualize.html\#code=class%20ListNode%3A%0A%20%20%20%20def%20\_\_init\_\_(self,%20x%29%3A%0A%20%20%20%20%20%20%20%20self.val%20%3D%20x%0A%20%20%20%20%20%20%20%20self.next%20%3D%20None%0Aclass%20LinkedList%3A%0A%20%20%20%20def%20\_\_init(self%29%3A%0A%20%20%20%20%20%20%20%20self.head%20%3D%20None%0A%0A%20%20%20%20def%20deserializeList(self,s%29%3A%0A%20%20%20%20%20%20%20%20l%20%3D%20s.split('-%3E'%29%0A%20%20%20%20%20%20%20%20nodes%20%3D%20map(lambda%20x%20%3A%20ListNode(x%29,%20l%29%0A%20%20%20%20%20%20%20%20dummy%20%3D%20ListNode(-100%29%0A%20%20%20%20%20%20%20%20dummy.next%20%3D%20nodes%5B0%5D%0A%20%20%20%20%20%20%20%20for%20i%20in%20range(len(nodes%29%20-%201%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20nodes%5Bi%5D.next%20%3D%20nodes%5Bi%2B1%5D%0A%20%20%20%20%20%20%20%20self.head%20%20%3D%20dummy.next%0A%0A%20%20%20%20def%20printList(self%29%3A%0A%20%20%20%20%20%20%20%20cur%20%3D%20self.head%0A%20%20%20%20%20%20%20%20while%20cur%20!%3D%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20print%20cur.val%0A%20%20%20%20%20%20%20%20%20%20%20%20cur%20%3D%20cur.next%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20def%20removeElements(self,%20head,%20val%29%3A%0A%20%20%20%20%23%20Write%20your%20code%20here%0A%20%20%20%20%20%20%20%20if%20head%20is%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20None%0A%0A%20%20%20%20%20%20%20%20dummy%20%3D%20ListNode(-100%29%0A%20%20%20%20%20%20%20%20dummy.next%20%3D%20head%0A%20%20%20%20%20%20%20%20pre%20%3D%20dummy%0A%20%20%20%20%20%20%20%20while%20head%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20if%20head.val%20%3D%3D%20val%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20pre.next%20%3D%20head.next%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20head%20%3D%20pre%0A%20%20%20%20%20%20%20%20%20%20%20%20pre%20%3D%20head%0A%20%20%20%20%20%20%20%20%20%20%20%20head%3D%20head.next%0A%20%20%20%20%20%20%20%20self.head%20%3D%20dummy.next%0A%0A%0AL%20%3D%20LinkedList(%29%0AL.deserializeList('1-%3E2-%3E3-%3E3-%3E4-%3E5-%3E3'%29%0A%23L.printList(%29%0AL.removeElements(L.head,%202%29%0AL.printList(%29&cumulative=false&curInstr=110&heapPrimitives=false&mode=display&origin=opt-frontend.js&py=2&rawInputLstJSON=%5B%5D&textReferences=false](http://www.pythontutor.com/visualize.html#code=class%20ListNode%3A%0A%20%20%20%20def%20__init__(self,%20x%29%3A%0A%20%20%20%20%20%20%20%20self.val%20%3D%20x%0A%20%20%20%20%20%20%20%20self.next%20%3D%20None%0Aclass%20LinkedList%3A%0A%20%20%20%20def%20__init(self%29%3A%0A%20%20%20%20%20%20%20%20self.head%20%3D%20None%0A%0A%20%20%20%20def%20deserializeList(self,s%29%3A%0A%20%20%20%20%20%20%20%20l%20%3D%20s.split()