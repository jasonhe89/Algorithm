```
from heapq import *
class Solution:
    \# @param matrix: a matrix of integers
    \# @param k: an integer
    \# @return: the kth smallest number in the matrix
    def kthSmallest(self, matrix, k):
        \# write your code here
        if not matrix:
            return 0

        heap = []
        row = len(matrix)
        col = len(matrix[0])

        for i in range(col):
            heappush(heap, (matrix[0][i], 0, i))

        for j in range(k-1):
            curr = heappop(heap)
            x = curr[1]
            y = curr[2]
            if x + 1 < row:
                heappush(heap, (matrix[x+1][y], x+1, y))

        return heap[0][0]
```