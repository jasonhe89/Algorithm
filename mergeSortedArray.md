```python
class Solution:
    #@param A and B: sorted integer array A and B.
    #@return: A new sorted integer array
    def mergeSortedArray(self, A, B):
        # write your code here
        C = [None] * (len(A) + len(B))
        nA = len(A) - 1
        nB = len(B) - 1
        nC = len(C) - 1
        while nA >= 0 and nB >= 0:
            if A[nA] > B[nB]:
                C[nC]  = A[nA]
                nA -= 1
            else:
                C[nC] = B[nB]
                nB -= 1
            nC -= 1
        if nA >= 0:
            C[:nA+1] = A[:nA+1]
        else:
            C[:nB+1] = B[:nB+1]
        return C
        
```