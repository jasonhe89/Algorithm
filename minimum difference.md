```python
def findMinDifference(nums):
    lst = sorted(nums)
    diff = sys.maxint
    for i in range(len(lst) - 1):
        newDiff = abs(lst[i+1] - lst[i])
        if newDiff < diff:
            diff = newDiff
    return newDiff
    
```