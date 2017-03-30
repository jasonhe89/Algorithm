```python
class Solution:
    # @param n: an integer
    # @return: a boolean which equals to True if the first player will win
    def firstWillWin(self, n):
        dp = [None] * (n + 1)
        
        return self.MemorySearch(n, dp)
        
    def MemorySearch(self, n, dp):
        if n == 0:
            return False
        if n == 1:
            return True
        if n == 2:
            return True
        if n == 3:
            return False
            
        if dp[n] != None:
            return dp[n]
        dp[n] = self.MemorySearch(n-2, dp) and self.MemorySearch(n-3, dp) or self.MemorySearch(n-3,dp) and self.MemorySearch(n-4, dp)

        return dp[n]
        
```

```python
class Solution:
    # @param n: an integer
    # @return: a boolean which equals to True if the first player will win
    def firstWillWin(self, n):
        dp = [None] * (n + 1)
        flag = [0] * (n+1)
        return self.MemorySearch(n,dp,flag)
        
    def MemorySearch(self, n, dp, flag):
        if n == 0:
            return False
        if n == 1:
            return True
        if n == 2:
            return True
        if n == 3:
            return False
        
        
        
        if flag[n] == 1:
            return dp[n]
        flag[n] = 1
        dp[n] = not self.MemorySearch(n-1,dp,flag) or not self.MemorySearch(n-2,dp,flag)
        
        return dp[n]
        
```