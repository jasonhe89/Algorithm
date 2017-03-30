```python
class Solution:
    # @param {int[]} A an integer array
    # @param {int} target an integer
    # @param {int} k a non-negative integer
    # @return {int[]} an integer array
    def kClosestNumbers(self, A, target, k):
        # Write your code here
        if A == []:
            return []
        lst = []
        start = 0
        end = len(A) - 1
        while start + 1 < end:
            mid = start + (end - start) / 2
            if A[mid] == target:
                end = mid
            elif A[mid] < target:
                start = mid
            elif A[mid] > target:
                end = mid
                
                
        if abs(A[start] - target) > abs(A[end] - target):
            start = end
            
        lst.append(A[start])
        l = 1
        r = 1
        for i in range(k-1):
            #print l
            if start - l < 0 and start + r >= len(A):
                break
            if start - l < 0:
                lst.append(A[start + r])
                r += 1
                continue
            if start + r >= len(A):
                lst.append(A[start - l])
                l += 1
                continue
            if abs(A[start - l] - target) == abs(A[start + r] - target):
                lst.append(A[start - l])
                l += 1
                continue
            elif abs(A[start - l] - target) < abs(A[start + r] - target):
                lst.append(A[start - l])
                l += 1 
                continue
            else:
                lst.append(A[start + r])
                r += 1
                continue
            
        return lst
```