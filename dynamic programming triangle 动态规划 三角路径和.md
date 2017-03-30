动态规划的基本分析和基础语法。

```java
public class Solution {
    /**
     * @param triangle: a list of lists of integers.
     * @return: An integer, minimum path sum.
     */
    int best = Integer.MAX_VALUE;  // global var to store best path
    public int minimumTotal(int[][] triangle) {
        // write your code here
    int n = triangle.length;
    
    
    traverse(n,0,0,0,triangle );
    return best;
    }
    //DFS : traverse to find the max path
    
    void traverse(int n, int x, int y, int sum, int[][] triangle){
        if(x == n){
          //found a whole path from top to bottom
          //base case
          if (sum < best){
            best = sum;
          }
          return;
        }
        
        traverse(n,x+1, y, sum + triangle[x][y],triangle);  //go down only
        traverse(n,x+1, y+1, sum + triangle[x][y],triangle); // go  down right
    }

}
```

python 动态规划的语法， f = {}

f[i,j] = ???

**trans: f[i,j] = min( f [i-1, j], f[i-1, j-1]) + triangle[i][j]**

利用dict 构建转移图。



```python
class Solution:
    """
    @param triangle: a list of lists of integers.
    @return: An integer, minimum path sum.
    """
    def minimumTotal(self, triangle):
        # write your code here
        # this is the version for top-down
        f = {}
        f[0,0]= triangle[0][0]
        for i in range(1,len(triangle)):
            f[i,0] = f[i-1,0] + triangle[i][0]
            f[i,i] = f[i-1, i-1] + triangle[i][i]
            
        for i in range(1,len(triangle)):
            for j in range(1,i):
                f[i,j] = min(f[i-1, j], f[i-1, j-1]) + triangle[i][j]
                
        lastRowLen = len(triangle) - 1    
        minLen = f[lastRowLen,0]
        
        for i in range(len(triangle)):
            minLen = min(minLen, f[lastRowLen, i])
            
        return minLenminlen
```