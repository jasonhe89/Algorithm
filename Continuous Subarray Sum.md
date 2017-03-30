比较下面段code 下标处理的异同

eg i = 1 时， start = 0, end = 1

表示前0项和， 前1 项和之差====\> a0 ==\> [0,0] 下标

eg a1,a2 ===\> [1,2] 下标

```python
class Solution:
    # @param {int[]} A an integer array
    # @return {int[]}  A list of integers includes the index of the 
    #                  first number and the index of the last number
    def continuousSubarraySum(self, nums):
        if len(nums) == 0:
            return [0,0]
        preSum = []
        preSum.append(0)
        for i in range(len(nums)):
            preSum.append(preSum[i] + nums[i])
        
        end = 1
        start = 0
        minIndxSoFar
        leastPreSum = sys.maxint
        maxSoFar = -(sys.maxint - 1) 
        for i, s in enumerate(preSum):
            if s - leastPreSum > maxSoFar:
                maxSoFar = s - leastPreSum
                end = i     #前i项和最大
                start = minIndexSoFar
        
        
```

注意start = 0, end = -1

```python
class Solution:
    ans = -sys.maxint + 1
    local = 0
    start, end = 0, -1
    result = [-1,-1]
    for x in A:
        if local < 0:
            local = x
            start = end + 1
            end = start
        else:
            local += x
            end += 1
        if local > ans:
            ans = local
            result = [start, end]
    return result
```

```python
class Solution:
    # @param {int[]} A an integer array
    # @return {int[]}  A list of integers includes the index of the 
    #                  first number and the index of the last number
    def continuousSubarraySum(self, nums):
        # Write your code here
        
     if len(nums) == 0:
         return [0,0]
        
        #pre sum
     preSum = []
     preSum.append(0)
     for i in range(len(nums)):
         preSum.append(preSum[i] + nums[i])
     
     end = 1
     start = 0
     minIndexSoFar = 0
     leastPreSum = sys.maxint
     maxSoFar = -(sys.maxint - 1)
     for i, s in enumerate(preSum):
        #更新当前最大的subarray Sum
         if s - leastPreSum > maxSoFar:
             maxSoFar = s - leastPreSum
             end = i
             start = minIndexSoFar
        #更新当前的最小前N项和
         if leastPreSum > s:
             leastPreSum = s
             minIndexSoFar = i
             #start = i
             
     return [start, end-1]
```