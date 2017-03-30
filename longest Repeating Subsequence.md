```python
#s='bcdaq'
#print(sorted(s))

class Solution:
    def longestRepeatingSubsequence(self, input_string):
        n = len(input_string)
        dp = [[0 for _ in range(n+1)] for _ in range(n+1)]
        print(dp)

        for i in range(1,n+1):
            for j in range(1,n+1):
                if input_string[i-1] == input_string[j-1] and i != j:
                    dp[i][j] = dp[i-1][j-1] + 1

                else:
                    dp[i][j] = max(dp[i][j-1], dp[i-1][j])

        for i in range(n+1):
            print(dp[i])
        print(dp[n][n])
        return dp[n][n]


s = Solution()
s.longestRepeatingSubsequence('aabcd')
```