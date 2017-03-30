```python
"""
Definition of ListNode
class ListNode(object):

    def __init__(self, val, next=None):
        self.val = val
        self.next = next
"""
class Solution:
    """
    @param lists: a list of ListNode
    @return: The head of one sorted list.
    """
    def mergeKLists(self, lists):
        # write your code here
        if len(lists) == 1:
            return None
        else:
            return self.mergeHelper(lists, 0, len(lists) - 1)
        
    #private ListNode mergeHelper(List<ListNode> lists, int start, int end)
    def mergeHelper(self, lists, start , end):
        #base case start == end
        if start == end:
            return lists[start]
        #divide
        mid = start + (end - start) / 2
        left = self.mergeHelper(lists, start, mid)
        right self.mergeHelper(lists, mid + 1, end)

        #conquer
        return self.mergeTwoLists(left, right)

    def mergeTwoLists(list1, list2):
        dummy = ListNode(0)
        temp = dummy
        while l1 != None and l2 != None:
            if l1.val < l2.val:
                temp.next = l1
                l1 = l1.next
            else:
                temp.next = l2
                l2 = l2.next
            temp = temp.next
        if l1 != None:
            temp.next = l1
        else:
            temp.next = l2
        return dummy.next
```