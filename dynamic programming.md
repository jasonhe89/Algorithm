```java
//DFS : traverse
void traverse(int x, int y, int sum){
    if(x == n){
      //found a whole path from top to bottom
      if (sum < best){
        best = sum;
      }
      return;
    }
    
    traverse(x+1, y, sum + A[x][y]);
    traverse(x+1, y+1, sum + A[x][y]);
}
  
best = MAXINT;
traverse(0,0,0);

```