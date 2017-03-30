**此题思路很巧，用了两个heap。
1\. 最大heap:：存放n/2 个比较小的数
2\. 最小堆：存放n/2 个比较大的数 －－－－查询最小值很快
3\. 需要保证最小堆的最小值大于最大堆的最大值。
4\. 每次读取一个新元素时，奇数次放最大堆，偶数次放最小堆，放完了再更新两个堆需要维持的属性（最小堆的最小值大于最大堆的最大值）**

**eg. 最大堆[4,2,3,1]
最小堆[5,6,7,8]
此时最大堆的最大值为中位数。**

```python
import heapq
class Solution:
    """
    @param nums: A list of integers.
    @return: The median of numbers
    """
    
    minHeap, maxHeap = [], []
    numbers = 0
    def medianII(self, nums):
        ans = []
        for item in nums:
            self.add(item)
            ans.append(self.getMedian())
        return ans
        
    
    def getMedian(self):
        return -self.maxHeap[0]   #返回左边最大堆的最大值－－－－median

    def add(self, value):
        if self.numbers % 2 == 0:
            heapq.heappush(self.maxHeap, -value)
        else:
            heapq.heappush(self.minHeap, value)
        self.numbers += 1
        
        if  len(self.minHeap) == 0:
            return
        if -self.maxHeap[0] > self.minHeap[0]:
            maxLeft = -self.maxHeap[0]
            minRight = self.minHeap[0]
            heapq.heapreplace(self.maxHeap, -minRight)
            heapq.heapreplace(self.minHeap, maxLeft)
        return
```

```python
import heapq
class Solution:
    minHeap, maxHeap = [], []
    numbers = 0
    def medianII(self, nums):
        ans = []
        for item in nums:
            self.add(item)
            ans.append(self.getMedian())
        return ans
        
    def getMedian(self):
        return -self.maxHeap[0]
        
    def add(self, value):
        if self.numbers % 2 == 0:
            heapq.heappush(self.maxHeap, -value)
        else:
            heapq.heappush(self.minHeap, value)
        if len(self.minHeap) == 0:
            return
        if -self.maxHeap[0] > self.minHeap[0]:
            maxLeft = -self.maxHeap[0]
            minRight = self.minHeap[0]
            heapq.heapreplace(self.maxHeap,-minRight)
            heapq.heapreplace(self.minHeap,maxLeft)
        return
```