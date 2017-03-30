sorter 的定义

自定义排序的用法

sorted(list, cop = sorter)

```python
"""
Definition of Interval.
class Interval(object):
    def __init__(self, start, end):
        self.start = start
        self.end = end
"""

def sorter(x, y):
    if x[0] != y[0]:
        return x[0] - y[0]
    return x[1] - y[1]
    
class Solution:
    # @param airplanes, a list of Interval
    # @return an integer
    def countOfAirplanes(self, airplanes):
        # write your code here
        tempList = []
        for point in airplanes:
            tempList.append((point.start, 1))
            tempList.append((point.end, -1))
            
        tempList = sorted(tempList, cmp=sorter)
        
        count = 0
        maxF = 0
        for point in tempList:
            if point[1] == 1:
                count += 1
            else:
                count -= 1
            maxF = max(maxF, count)
            
        return maxF
```