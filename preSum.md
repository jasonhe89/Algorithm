```python
# write your code here
preSum = [None] * len(nums) 
preSum[0]=nums[0]
 
for i in range(1,len(nums)):
  preSum[i] = preSum[i-1] + nums[i]
maxSum = max(preSum)
minSum = min(preSum)
return maxSum - minSum
```