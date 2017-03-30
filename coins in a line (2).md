```python
int[][] dp = new int[n+1][n+1]

for (int i =0; i <n ; ++i){
    dp[i][i] = values[i];
  }
  
len [2,n)
i [0,n)
  if j>= n
  continue
dp[i][j] = max (s[i][j] - dp[i+1][j], .....
```