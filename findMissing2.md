```python
class Solution:
    # @param {int} n an integer
    # @param {string} str a string with number from 1-n
    #                     in random order and miss one number
    # @return {int} an integer
    def findMissing2(self, n, st):
        # Write your code here
        if n == 0:
            return -1
        self.lst = map(str, range(1, n + 1))
        return self.helper(n, st)
        
    def helper(self, n, str):
        if n < 0:
            return -1
        if self.lst[n-1] not in str:
            return self.lst[n-1]
        left = self.helper(n-1, str.replace(self.lst[n-1],""))
        right = self.helper(n-1, str)
        if left != -1 and right != -1:
            return -1
        if left == -1:
            return right
        else:
            return left
```