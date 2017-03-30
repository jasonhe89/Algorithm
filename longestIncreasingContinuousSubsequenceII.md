

```python
class Solution:
    def search(x, y, A):
        dx = [1,-1,0,0]
        dy = [0,0,1,-1]
        if self.flag[x][y] != 0:
            return self.dp[x][y]
    
        ans = 1
        for i in range(4):
            nx = x + self.dx[i]
            ny = y + self.dy[i]
        
            if 0 <= nx and nx < self.n and 0 <= ny and ny < self.m:
                if A[x][y] > A[nx][ny] :
                    ans = max(ans, self.search(nx,ny,A) + 1)
        
        self.flag[x][y] = 1
        self.dp[x][y] = ans
        return ans
        
    def longestIncreasingContinuousSubsequenceII(self, A):
        if len(A) == 0 or A is None:
            return 0
        
        self.n = len(A)
        self.m = len(A[0])
        ans = 0
        self.dp = [[0] * self.m for _ in range(self.n)]
        self.flag = [[0] * self.m for _ in range(self.n)]
        
        for i in range(self.n):
            for j in range(self.m):
                self.dp[i][j] = self.search(i,j, A)
                ans = max(ans, self.dp[i][j])
                
        return ans
```

可视化链接

[http://www.pythontutor.com/visualize.html\#code=class%20Solution%3A%0A%20%20%20%20%23%20%40param%20%7Bint%5B%5D%5B%5D%7D%20A%20an%20integer%20matrix%0A%20%20%20%20%23%20%40return%20%7Bint%7D%20%20an%20integer%0A%20%20%20%20%0A%20%20%20%20def%20longestIncreasingContinuousSubsequenceII(self,%20A%29%3A%0A%20%20%20%20%20%20%20%20if%20len(A%29%20%3D%3D%200%20or%20A%20is%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%200%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20self.n%20%3D%20len(A%29%0A%20%20%20%20%20%20%20%20self.m%20%3D%20len(A%5B0%5D%29%0A%20%20%20%20%20%20%20%20ans%20%3D%200%0A%20%20%20%20%20%20%20%20self.dp%20%3D%20%5B%5B0%5D%20\*%20self.m%20for%20\_%20in%20range(self.n%29%5D%0A%20%20%20%20%20%20%20%20self.flag%20%3D%20%5B%5B0%5D%20\*%20self.m%20for%20\_%20in%20range(self.n%29%5D%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20for%20i%20in%20range(self.n%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20j%20in%20range(self.m%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.dp%5Bi%5D%5Bj%5D%20%3D%20self.search(i,j,%20A%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20ans%20%3D%20max(ans,%20self.dp%5Bi%5D%5Bj%5D%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20return%20ans%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20def%20search(self,%20x,%20y,%20A%29%3A%0A%20%20%20%20%20%20%20%20dx%20%3D%20%5B1,-1,0,0%5D%0A%20%20%20%20%20%20%20%20dy%20%3D%20%5B0,0,1,-1%5D%0A%20%20%20%20%20%20%20%20if%20self.flag%5Bx%5D%5By%5D%20!%3D%200%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.dp%5Bx%5D%5By%5D%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20ans%20%3D%201%0A%20%20%20%20%20%20%20%20for%20i%20in%20range(4%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20nx%20%3D%20x%20%2B%20dx%5Bi%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20ny%20%3D%20y%20%2B%20dy%5Bi%5D%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20if%200%20%3C%3D%20nx%20and%20nx%20%3C%20self.n%20and%200%20%3C%3D%20ny%20and%20ny%20%3C%20self.m%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20A%5Bx%5D%5By%5D%20%3E%20A%5Bnx%5D%5Bny%5D%20%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20ans%20%3D%20max(ans,%20self.search(nx,ny,A%29%20%2B%201%29%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20self.flag%5Bx%5D%5By%5D%20%3D%201%0A%20%20%20%20%20%20%20%20self.dp%5Bx%5D%5By%5D%20%3D%20ans%0A%20%20%20%20%20%20%20%20return%20ans%0A%20%20%20%20%20%20%20%20%0As%20%3D%20Solution(%29%0AA%20%3D%5B%5B1%20,2%20,3%20%5D,%5B24,23,6%5D,%20%5B25,22,7%5D%5D%0Ax%20%3D%20s.longestIncreasingContinuousSubsequenceII(A%29&cumulative=false&curInstr=395&heapPrimitives=false&mode=display&origin=opt-frontend.js&py=2&rawInputLstJSON=%5B%5D&textReferences=false](http://www.pythontutor.com/visualize.html#code=class%20Solution%3A%0A%20%20%20%20%23%20%40param%20%7Bint%5B%5D%5B%5D%7D%20A%20an%20integer%20matrix%0A%20%20%20%20%23%20%40return%20%7Bint%7D%20%20an%20integer%0A%20%20%20%20%0A%20%20%20%20def%20longestIncreasingContinuousSubsequenceII(self,%20A%29%3A%0A%20%20%20%20%20%20%20%20if%20len(A%29%20%3D%3D%200%20or%20A%20is%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%200%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20self.n%20%3D%20len(A%29%0A%20%20%20%20%20%20%20%20self.m%20%3D%20len(A%5B0%5D%29%0A%20%20%20%20%20%20%20%20ans%20%3D%200%0A%20%20%20%20%20%20%20%20self.dp%20%3D%20%5B%5B0%5D%20*%20self.m%20for%20_%20in%20range(self.n%29%5D%0A%20%20%20%20%20%20%20%20self.flag%20%3D%20%5B%5B0%5D%20*%20self.m%20for%20_%20in%20range(self.n%29%5D%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20for%20i%20in%20range(self.n%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20for%20j%20in%20range(self.m%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20self.dp%5Bi%5D%5Bj%5D%20%3D%20self.search(i,j,%20A%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20ans%20%3D%20max(ans,%20self.dp%5Bi%5D%5Bj%5D%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20return%20ans%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20def%20search(self,%20x,%20y,%20A%29%3A%0A%20%20%20%20%20%20%20%20dx%20%3D%20%5B1,-1,0,0%5D%0A%20%20%20%20%20%20%20%20dy%20%3D%20%5B0,0,1,-1%5D%0A%20%20%20%20%20%20%20%20if%20self.flag%5Bx%5D%5By%5D%20!%3D%200%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20self.dp%5Bx%5D%5By%5D%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20ans%20%3D%201%0A%20%20%20%20%20%20%20%20for%20i%20in%20range(4%29%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20nx%20%3D%20x%20%2B%20dx%5Bi%5D%0A%20%20%20%20%20%20%20%20%20%20%20%20ny%20%3D%20y%20%2B%20dy%5Bi%5D%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20if%200%20%3C%3D%20nx%20and%20nx%20%3C%20self.n%20and%200%20%3C%3D%20ny%20and%20ny%20%3C%20self.m%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20A%5Bx%5D%5By%5D%20%3E%20A%5Bnx%5D%5Bny%5D%20%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20ans%20%3D%20max(ans,%20self.search(nx,ny,A%29%20%2B%201%29%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20self.flag%5Bx%5D%5By%5D%20%3D%201%0A%20%20%20%20%20%20%20%20self.dp%5Bx%5D%5By%5D%20%3D%20ans%0A%20%20%20%20%20%20%20%20return%20ans%0A%20%20%20%20%20%20%20%20%0As%20%3D%20Solution(%29%0AA%20%3D%5B%5B1%20,2%20,3%20%5D,%5B24,23,6%5D,%20%5B25,22,7%5D%5D%0Ax%20%3D%20s.longestIncreasingContinuousSubsequenceII(A%29&cumulative=false&curInstr=395&heapPrimitives=false&mode=display&origin=opt-frontend.js&py=2&rawInputLstJSON=%5B%5D&textReferences=false)