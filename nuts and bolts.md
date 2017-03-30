```python
# class Comparator:
#     def cmp(self, a, b)
# You can use Compare.cmp(a, b) to compare nuts "a" and bolts "b",
# if "a" is bigger than "b", it will return 1, else if they are equal,
# it will return 0, else if "a" is smaller than "b", it will return -1.
# When "a" is not a nut or "b" is not a bolt, it will return 2, which is not valid.
class Solution:
    def sortNutsAndBolts(self, nuts, bolts, compare):
        self.quickSort(nuts,bolts,0, len(nuts)-1, compare)
    
    
    def quickSort(self, nuts, bolts, left, right, compare):
        if left >= right:
            return
        index = self.partition(nuts, bolts[left],left,right, compare)
        self.partition(botls,nuts[index], left,right, compare)
        self.quickSort(nuts,bolts,left, index -1, compare)
        self.quickSort(nuts,bolts, index +1 , right, compare)
    
    def partition(self, lst, pivot, l, u, compare):
        for i in range(l,u+1):
            if compare.cmp(lst[i],pivot) == 0 or compare.cmp(pivot, lst[i])==0:
                lst[i], lst[l] = lst[l], lst[i]
                break
        now = lst[l]
        left = l 
        right = u
        while left < right:
            while left < right and (compare.cmp(lst[right],pivot) == 1 or compare.cmp(pivot, lst[right]) == -1):
                right -= 1
            lst[left] = lst[right]
            while left < right and (compare.cmp(lst[left],pivot) == -1 or compare.cmp(pivot, lst[left]) == 1):
                left += 1
            lst[right] = lst[left]
            
        lst[left] = now
        
        return left
```