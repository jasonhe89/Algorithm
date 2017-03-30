```python
class Solution:
    def pal():
        
        for i in range(n):
            P[i][i] = True
            C[i][i] = 0
        
        for l in range(2, n+1):
            for i in range(n - l + 1):
                j = i + l - 1
                if l == 2:
                    P[i][j] = ( s[i] == s[j])
                else:
                    P[i][j] = (s[i] == s[j]) and P[i+1][j-1]
                if P[i][j] == True:
                    C[i][j] = 0
                else:
                    c[i][j] = sys.maxint
                    for k in range(i,j):
                        C[i][j] = min(C[i][j], C[i][k] + C[k+1][j] + 1)
        return C[0][n-1]
        
        
        for l in range(2, n+1):
            for i in range(n - l + 1):
                j = i + l - 1
                if l == 2:
                    P[i][j] = ( s[i] == s[j])
                else:
                    P[i][j] = (s[i] == s[j]) and P[i+1][j-1]
        
        for i in range(n):
            if P[0][i] = True:
                C[i] = 0
            else:
                C[i] = sys.maxint
                for j in range(i):
                    if P[j+1][i] == True and 1 + C[j] < C[i]:
                        C[i] = 1 + C[j]
                        
        return C[n-1]
        
```

```python
class Solution:
    # @param {string} s input string
    # @return {string} the longest palindromic substring
    def longestPalindrome(self, s):
        n = len(s)
        t = [[False] * n for _ in range(n)]
        maxLength = 1
        for i in range(n):
            t[i][i] = True
        start = 0
        for i in range(n):
            if s[i] == s[i+1]:
                t[i][i+1] = True
                start = i
                maxLength = 2
        for k in range(3,n+1):
            for i in range(n-k+1):
                j = i + k - 1
                if t[i+1][j-1] == True and s[i] == s[j]:
                    t[i][j] = True
                if k > maxLength:
                    start = i
                    maxLength = k
        return s[start, start + maxLength -1]
```