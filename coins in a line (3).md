```python
class Solution:
    # @param values: a list of integers
    # @return: a boolean which equals to True if the first player will win
    def firstWillWin(self, values):
        self.dp = [None] * (len(values) + 1)
        
        total = sum(values)
        return self.helper(values) > (0.5 * total)
        
    def helper(self, values):
        # write your code here
        if len(values) <= 0:
            return 0
        if len(values) <= 2:
            return sum(values)
        if self.dp[len(values)] != None:
            return self.dp[len(values)]
        first = min(self.helper(values[2:len(values)]),self.helper(values[3:len(values)])) + values[0]
        
        second = min(self.helper(values[3:len(values)]),self.helper(values[4:len(values)])) + values[0] + values[1]
        self.dp[len(values)] = max(first, second)
        return self.dp[len(values)]
```