```java
class Solution:
    """
    @param {int} n a integer
    @return {int} a integer
    """
    def climbStairs2(self, n):
        # Write your code here
        if n < 0:
            return 1
        if n == 0:
            return 1
        if n <= 2:
            return n
        
        # first stair 1 choice
        # second stairs 2 c {11, 2}
        #3 stairs {111,12,21}
        #4 stairs {1111,112,121,13,211,31,22}
        result = [1,2,4]
        for i in range(n-3):
            result.append(result[-3] + result[-2] + result[-1])
            
        return result[-1]

```