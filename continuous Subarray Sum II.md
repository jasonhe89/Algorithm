<https://lefttree.gitbooks.io/leetcode/content/highFreq/continuousSubarraySum2.html>

[https://algorithm.yuanbin.me/zh-hans/problem\_misc/continuous\_subarray\_sum.html](https://algorithm.yuanbin.me/zh-hans/problem_misc/continuous_subarray_sum.html)

总结：利用局部sum 和全局sum 来 求得最大continuous sum 和其下标。

 利用局部sum 和全局sum 来 求得最小continuous sum 和其下标。

再细心处理的到环的最大子数组。

注意以下算法start =0 , end =-1

```python
class Solution:
    # @param {int[]} A an integer array
    # @return {int[]}  A list of integers includes the index of the 
    #                  first number and the index of the last number
    def continuousSubarraySumII(self, A):
        # Write your code here
        ans = -sys.maxint + 1
        local = 0
        total = 0
        start, end = 0, -1
        result = [-1,-1]
        for x in A:
            total += x
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
        #print result
        local = 0
        start ,end =0, -1
        minAns = sys.maxint
        minResult = [-1,-1]
        for x in A:
            if local > 0:
                local = x
                start = end + 1
                end = start
            else:
                local += x
                end += 1
            if local < minAns:
                minAns = local
                minResult = [start,end]
        
        if total < 0 and ans < 0:
            return result
        if total - minAns < ans:
            return result
        else:
            return [(minResult[1] + 1) % len(A), (minResult[0] -1 ) % len(A)]
        
```

```python
def continuousSubarraysSumII(self, A):
    ans = -sys.maxint + 1
    sum, total = 0, 0
    start, end = 0, -1
    result = [-1,-1]
    length = len(A)
    for x in A:
        total += x
        if sum < 0:
            start = end + 1
            end = start
        else:
            sum += x
            end += 1
        if sum > ans:
            ans = sum
            result = [start, end]
    
    start, end = 0, -1
    sum = 0
    for x in A:
        if sum > 0:
            sum = x
            start = end + 1
            end = start
        else:
            sum += x
            end += 1
        if start == 0 and end == length - 1:
            continue
        if total - sum > ans:
            ans = total - sum
            result = [(end + 1) % length, (start - 1 + length) % length]
    return result
```

```python
def continuousSubarraySumII(self, A):
  result = [0,0]
  total = 0
  length = len(A)
  start = 0
  end = 0
  local = 0
  globalV = -sys.maxint + 1
  for i in range(length):
    total += A[i]
    if local < 0:
      local = A[i]
      start = i
      end = i
    else:
      local += A[i]
      end = i
    if local >= globalV:
      globalV = local
      result[0] = start
      result[1] = end
      
  local = 0
  start = 0
  end = -1
  for i in range(length):
    if local > 0:
      local = A[i];
      start = i
      end = i
    else:
      local += A[i]
      end = i
    if start == 0 and end == length -1:
      continue
    if total - local >= globalV:
      globalV = total - local
      result[0] = (end + 1) % length
      result[1] = (start - 1 + length) % length
      
  return result
  
  
  
```

Continuous Subarray Sum II
==========================

Question
--------

Given an integer array, find a continuous subarray where the sum of numbers is the biggest. Your code should return the index of the first number and the index of the last number. (If their are duplicate answer, return anyone)

Example Give `[-3, 1, 3, -3, 4]`, return `[1,4]`.

Thoughts
--------

### 方法1

* 按I的方法求出的结果
* 从整个array中减去中间最小的subarray，需要rotate的array

思路是这样的，像楼上说的两种情况，不rotate的 和rorate的。不rotate的和Continuous Subarray Sum I做法一样，不说了。rotate的，可以这样想，rotate的结果其实相当于是把原来的array中间挖了一段连续的array，那么挖哪一段呢？肯定是和最小的一段连续array。这样解法就出来了。

类似Continuous Subarray Sum I，在I里面是找到连续和最大的一段subarray，在这里，不仅找到和最大的一段连续array，并且也找到和最小的一段连续array，然后用整个array的sum减去这个最小的和，如果大于不rotate的最大和，那么解就是挖去的这段array的（尾+1， 头-1）

有一个edge case就是当array全部为负时，要挖去的array就是整个array，这个要注意一下。

### 方法2

首尾可以相连的题目可以想到在array的尾部再加上另一个copy,然后用I的方法求结果，但是要注意长度不能超过原有array的长度

Solution
--------

```
class Solution:
    \# @param {int[]} A an integer array
    \# @return {int[]} A list of integers includes the index of the 
    \# first number and the index of the last number
    def continuousSubarraySumII(self, A):
        \# Write your code here
        if not A:
            return 0
        currentSum = 0
        length = len(A)
        maxSum = sys.maxint * -1
        maxStart = 0
        maxEnd = 0
        maStart = 0

        minSum = sys.maxint
        minStart = 0
        minEnd = 0
        curMinSum = 0
        miStart = 0

        totalSum = 0
        for i in range(length):
            totalSum += A[i]
            if currentSum < 0:
                currentSum = A[i]
                maStart = i
            else:
                currentSum += A[i]

            if curMinSum > 0:
                curMinSum = A[i]
                miStart = i
            else:
                curMinSum += A[i]

            if maxSum < currentSum:
                maxSum = currentSum
                maxStart = maStart
                maxEnd = i

            if minSum > curMinSum:
                minSum = curMinSum
                minStart = miStart
                minEnd = i

        \#take care of the situation that all the elements are negative
        if totalSum - minSum > maxSum and minEnd != length - 1 and minStart != 0:
            start = minEnd + 1
            end = minStart - 1
        else:
            start = maxStart
            end = maxEnd

        return [start, end]
```