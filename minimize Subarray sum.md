preSum method, 注意下标

```python
class Solution:
     # @param nums: a list of integers
     # @param s: an integer
     # @return: an integer representing the minimum size of subarray
    def minimumSize(self, nums, s):
        # write your code here
        if len(nums) == 0:
            return -1
        n = len(nums)
        preSum = [0] * (n+1)
        preSum[0] = 0
        for i in range(n):
            preSum[i+1] += preSum[i] + nums[i]
            
        #print preSum
        length = sys.maxint
        
        for i in range(n):
            j = i
            while j < n + 1:
                #print j
                if preSum[j] - preSum[i] < s:
                    j += 1
                # update j state
                else:
                    #print i-j
                    length = min(length, j-i)
                    break
                #update i state
            
        if length == sys.maxint:
            return -1
        return length
            
```