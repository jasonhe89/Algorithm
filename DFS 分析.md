

```python
    def helper(self,nums,lst,result,visited):
        if len(nums) == len(lst):
            if lst not in result:
                result.append(list(lst))
            return
        for i in range(len(nums)):
            if visited[i] == True:
                continue
            lst.append(nums[i])
            visited[i] = True
            self.helper(nums, lst, result, visited)
            lst.pop()
            visited[i] = False
        return
        

```

```python
#排列组合的题目

class Solution:
    def permute(self, nums):
        result = []
        lst = []
        visited = [False] * len(nums)
        self.helper(nums,lst, result, visited)
        return result
        
        
    def helper(self,nums,lst,result,visited):
        if len(nums) == len(lst):
            if lst not in result:
                result.append(list(lst))
            return
        for i in range(len(nums)):
            if visited[i] == True:
                continue
            lst.append(nums[i])
            visited[i] = True
            self.helper(nums, lst, result, visited)
            lst.pop()
            visited[i] = False
        return
s = Solution()
p = s.permute([1,2,2,3,4])

核心函数解析：深度优先搜索nums 序列，eg [1,2,3,4]
步骤模拟，首先选取1放入到lst中，然后dfs 剩下三个数所组成的全部的排列......
完成产生所有的以1开头的全排列后回溯，pop 1, 选取2放入到lst 中，然后dfs 剩下三个数所组成的全部排列。

helper函数的定义是创造出visited 中还剩下的数的全排列。
base case: 只剩一个数，那么就是该数

```

```python
class Solution:
    def comb(self, nums):
        result = []
        lst = []
        self.helper(nums,lst, result, 0)
        return result
        
        
    def helper(self,nums,lst,result,index):
        if index == len(nums):
            if lst not in result:
                result.append(list(lst))
            return
        lst.append(nums[index])
        self.helper(nums,lst,result,index + 1)
        lst.pop()
        self.helper(nums,lst,result,index + 1)
        return
s = Solution()
p = s.comb([1,2,3,4])
```

```python
class Solution:
    # @param s, a string
    # @return a list of lists of string
    def partition(self,s):
        self.result = []
        self.dfs(s, [])
        return self.result
        
    def dfs(self, s, stringlist):
        if len(s) == 0:
            self.result.append(stringlist)
        for i in range(1, len(s) + 1):
            if self.isPalindrome(s[:i]):     #测试s 的前n 位是不是回文
                self.dfs(s[i:], stringlist + [s[:i]])
        
    def isPalindrome(self,s):
        for i in range(len(s)):
            if s[i] != s[len(s) - 1 -i]:return False
        return True

核心解析：
```