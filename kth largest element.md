利用填坑的partition， 每次找到一个p, 该p 的位置在排序好的数组固定， 如果p == len(A) -k 那么p位置的元素即是第k 大，如果p \< len(A) - k ,那么A[p] \< 第k 大元素，所有继续 parittion 右边的元素， 同理\>情况

```python
class Solution:
    # @param k & A a integer and an array
    # @return ans a integer
    def kthLargestElement(self, k, A):
        p = self.helper(k, A, 0, len(A) - 1)
        return A[p]
    
    def helper(self, k, A, l, r):
        if l >= r:
            return l
            
        p = self.partition(A, l, r)
        #print p
        if p == (len(A) - k):
            return p
        elif p > (len(A) - k) :
            return self.helper(k, A, l, p - 1)
        else:
            return self.helper(k, A, p+1, r)
         
    
    def partition(self, A, l ,r):
        pivot = A[l]
        while l < r:
            while l < r and A[r] >= pivot:
                r -= 1
            A[l] = A[r]
            while l < r and A[l] <= pivot:
                l += 1
            A[r] = A[l]
        
        A[l] = pivot
        return l
        
```