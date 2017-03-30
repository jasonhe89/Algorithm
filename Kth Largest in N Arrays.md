**样例**

n = `2` 数组 `[[9,3,2,4,7],[1,2,3,4,8]]`, 第三大元素是 `7`.

n = `2` 数组 `[[9,3,2,4,8],[1,2,3,4,2]]`, 最大数是 `9`, 次大数是 `8`, 第三大数是 `7`

```

```

先排序，再用heap 关键代码

```

class Node:
    def __init__(self, _v, _id, _i):
        self....
    def __cmp__(self,obj):
        return cmp(obj.value, self.value)

for i, array in enumerate(arrays):
    form_id = i
    index = len(array)- 1
    array.sort()
    if index >= 0:
        value = arrays[i][index]
        heapq.heappush(queue, Node(value, from_id, index)
```

```python

class Node:
    
    def __init__(self, _v, _id, _i):
        self.value = _v
        self.from_id = _id
        self.index = _i

    def __cmp__(self, obj):
        return cmp(obj.value, self.value)

import heapq

class Solution:
    # @param {int[][]} arrays a list of array
    # @param {int} k an integer
    # @return {int} an integer, K-th largest element in N arrays
    def KthInArrays(self, arrays, k):
        # Write your code here
        queue = []
        heapq.heapify(queue) 
        n = len(arrays)
        for i, array in enumerate(arrays):
            from_id = i
            index = len(array) - 1
            array.sort()
            if index >= 0:
                value = arrays[i][index]
                heapq.heappush(queue, Node(value, from_id, index))

        for i in xrange(k):
            node = heapq.heappop(queue)
            value = node.value
            from_id = node.from_id
            index = node.index

            if i == k-1:
                return value

            if index:
                index -= 1
                value = arrays[from_id][index]
                heapq.heappush(queue, Node(value, from_id, index))
```