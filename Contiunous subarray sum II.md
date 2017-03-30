解题：利用subarry sum 的贪心算法，拓展为既可以找到最大值，又可以找到index 的函数

先利用helper 函数找到中间连续某段的最大值

再利用挖去的思想找到中间连续某段的最小值

转化为原数组 ＊ －1 ==\>连续某段的最大值

但要注意数组全为负数的边界条件！

此时\* -1 之后， 我们会做出挖掉整个array 的选择，而题目要求至少选一个数，所以要分类讨论！

```python
class Solution:
    # @param {int[]} A an integer array
    # @return {int[]}  A list of integers includes the index of the 
    #                  first number and the index of the last number
    def continuousSubarraySumII(self, A):
        # Write your code here
        total = sum(A)
        notCross, notCrossTotal = self.helper(A)
        z = map(lambda x : -1 * x, A)
        cross, crossTotal = self.helper(z)
        #print notCross, notCrossTotal
        #print cross, crossTotal
        if crossTotal == -total:
            return notCross
        if total + crossTotal > notCrossTotal:
            return [cross[1] + 1, cross[0] - 1]
        else:
            return notCross
        
        
        
    def helper(self,A):
        local, total = 0, -(sys.maxint -1) 
        result = [0, 0]
        start, end = 0, 0
        for i in range(len(A)):
            if local < 0:
                local = A[i]
                start = i
                end = i
            else:
                local += A[i]
                end = i
            if local > total :
                total = local
                result = [start, end]
                
        return result, total
```

```python
def helper(self,A):
        local, total = 0, -(sys.maxint -1) 
        result = [0, 0]
        start, end = 0, 0
        for i in range(len(A)):
            if local < 0:
                local = A[i]
                start = i
                end = i
            else:
                local += A[i]
                end = i
            if local > total :
                total = local
                result = [start, end]
            
        return result
```

```python
def helper(self, A):
        local, total = 0, -(sys.maxint -1) 
        for i in range(len(A)):
            if local < 0:
                local = A[i]
            else:
                local += A[i]
            if local > total :
                total = local
            
        return total
```