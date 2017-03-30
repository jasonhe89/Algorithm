DFS 深度优先搜索解法。

```java
class Solution:
    # @param {boolean[][]} grid a boolean 2D matrix
    # @return {int} an integer
    def numIslands(self, grid):
        # Write your code here
        self.m = len(grid)
        if self.m == 0:
            return 0
        self.n = len(grid[0])
        if self.n == 0:
            return 0
            
        ans = 0
        
        for i in range(self.m):
            for j in range(self.n):
                if grid[i][j] == 0:
                    continue
                ans += 1
                self.dfs(grid, i , j)
        return ans
        
    def dfs(self, grid, i, j):
        if i < 0 or i >= self.m or j >= self.n or j < 0:
            return 
        if grid[i][j] == True:
            grid[i][j] = False
            self.dfs(grid, i - 1, j)
            self.dfs(grid, i, j - 1)
            self.dfs(grid, i+1, j)
            self.dfs(grid, i, j+1)
```