题意：给一个序列，一个目标值， 找到序列中某一段和 \>= 目标值，要求找到最短的那个序列。
注意此题的条件：所有数都是整数，目标也是整数，所以前N项和是递增的！
解题思路：
因为是找subarray Sum 所以自然而然的想到了前N项和数组(PREFIX SUM)。
首先i，j从0开始，j一直加，找到SUM[J] - SUM[0] \>= TARGET的J, 即前j项和满足条件。
eg Sum[5] 为前5项和 == nums[0] + nums[1] +..nums[4]
之后将i 向后挪动一位，在看 SUM[j] - SUM[i]是否满足。 即
(nums[0] + nums[1] +...nums[j-1] ) - (nums[0] + nums[1] +..num[i-1])
即 nums[i] +.. nums[j-1]
假设nums[-1] = 0
i = 0 时， SUM[0] = NUMS[-1]
i = 1 .... sum[1] = nums[0]
i = 2..... sum[2] = nums[0] + nums[1]

注意为什么length 是 j - i :
1画图来理解
2假如 NUM[0] = 7， 那么 j = 1 时， preSum[1] - preSum[0] == 7, 所以长度为j - i = 1， 子数组包含一个数。
index 为 【0，0】

```
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
        #得到prefixsum 数组
        #print preSum
        length = sys.maxint
        j = 0 
        for i in range(n):
            #j = i
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

```python
class Solution:
     # @param nums: a list of integers
     # @param s: an integer
     # @return: an integer representing the minimum size of subarray
    def minimumSize(self, nums, s):
        # write your code here
        if len(nums) == 0:
            return -1
        
        accSum = [0] * (len(nums) + 1)
        for i in range(len(nums)):
            accSum[i+1] = accSum[i] + nums[i]
        #print accSum
        length = sys.maxint
        j = 0 
        for i in range(len(accSum) - 1):
            while j < len(accSum):
                if accSum[j] - accSum[i] < s:
                    j += 1
                else:
                    length = min(length, j - i)
                    break
            
        
        if length != sys.maxint:
            return length
        
        return -1
```