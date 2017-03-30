```python
class Solution:
    """
    @param matrix, a list of lists of integers
    @param target, an integer
    @return a boolean, indicate whether matrix contains target
    """
    def searchMatrix(self, matrix, target):
        # write your code here
        if len(matrix) == 0:
            return False
        start = 0
        end = len(matrix) - 1
        mid = start + (end - start) / 2
        startRow = 0
        endRow = len(matrix[0]) - 1 
        # eg [1,2,3,4] start = 0 end = 3 mid = 3/2 = 1,  ---- 0-1, 2-3.
        while start + 1 < end:
            mid = start + (end - start) / 2
            if matrix[mid][0] == target:
                start = mid
                return True
            elif matrix[mid][0] > target:
                end = mid 
            elif matrix[mid][0] < target:
                start = mid
        if matrix[start][0] <= target and matrix[end][0] > target:
            while startRow + 1 < endRow:
                mid = startRow + (endRow - startRow) / 2
                if matrix[start][mid] == target:
                    return True
                elif matrix[start][mid] > target:
                    endRow = mid
                elif matrix[start][mid] < target:
                    startRow = mid
        if matrix[start][startRow] == target or matrix[start][endRow] == target:
            return True
        else:
            return False
```

```python

```