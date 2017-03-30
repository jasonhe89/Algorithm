```python
import math
import sys

class Solution:
    # @param {int} n a positive integer
    # @return {int} an integer
    def numSquares(self, n):
        if n <= 0 :
            return 0
        # Write your code here
        dp = [sys.maxint for _ in range(n+1)]
        dp[1] = 1
        
        for i in range(2,n+1):
            if self.is_square(i):
                dp[i] = 1
            else:
                for j in range(1, int(i ** 0.5)):
                    dp[i] = min(dp[i], dp[i-j*j] + 1)
                
        #print dp
        return dp[n]
            
                
                
    def is_square(self,integer):
        root = math.sqrt(integer)
        if int(root + 0.5) ** 2 == integer: 
            return True
        else:
            return False

        
```