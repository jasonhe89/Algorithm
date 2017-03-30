原题链接: <http://oj.leetcode.com/problems/maximum-subarray/> 
这是一道非常经典的动态规划的题目，用到的思路我们在别的动态规划题目中也很常用，以后我们称为”局部最优和全局最优解法“。
基本思路是这样的，在每一步，我们维护两个变量，一个是全局最优，就是到当前元素为止最优的解是，一个是局部最优，就是必须包含当前元素的最优的解。接下来说说动态规划的递推式（这是动态规划最重要的步骤，递归式出来了，基本上代码框架也就出来了）。假设我们已知第i步的global[i]（全局最优）和local[i]（局部最优），那么第i+1步的表达式是：
local[i+1]=Math.max(A[i], local[i]+A[i])，就是局部最优是一定要包含当前元素，所以不然就是上一步的局部最优local[i]+当前元素A[i]（因为local[i]一定包含第i个元素，所以不违反条件），但是如果local[i]是负的，那么加上他就不如不需要的，所以不然就是直接用A[i]；
global[i+1]=Math(local[i+1],global[i])，有了当前一步的局部最优，那么全局最优就是当前的局部最优或者还是原来的全局最优（所有情况都会被涵盖进来，因为最优的解如果不包含当前元素，那么前面会被维护在全局最优里面，如果包含当前元素，那么就是这个局部最优）。

接下来我们分析一下复杂度，时间上只需要扫描一次数组，所以时间复杂度是O(n)。空间上我们可以看出表达式中只需要用到上一步local[i]和global[i]就可以得到下一步的结果，所以我们在实现中可以用一个变量来迭代这个结果，不需要是一个数组，也就是如程序中实现的那样，所以空间复杂度是两个变量（local和global），即O(2)=O(1)。
代码如下： 

**[java]** [view plain](http://blog.csdn.net/linhuanmars/article/details/21314059# "view plain") [copy](http://blog.csdn.net/linhuanmars/article/details/21314059# "copy")

 [![在CODE上查看代码片](resources/BA3ACBF6D7A3420D26DB10207385A617.png)](https://code.csdn.net/snippets/246227 "在CODE上查看代码片")[![派生到我的代码片](resources/02725C4F62B67DC23F2B87E776850078.svg)](https://code.csdn.net/snippets/246227/fork "派生到我的代码片")

1. public int maxSubArray(int[] A) {
2. if(A==null || A.length==0)
3. return 0;
4. int global = A[0];
5. int local = A[0];
6. for(int i=1;i\<A.length;i++)
7. {
8. local = Math.max(A[i],local+A[i]);
9. global = Math.max(local,global);
10. }
11. return global;
12. }

这道题虽然比较简单，但是用到的动态规划方法非常的典型，我们在以后的题目中还会遇到，大家还是要深入理解一下哈。我现在记得的用到的题目是[Jump Game](http://blog.csdn.net/linhuanmars/article/details/21354751)，以后有统计一下再继续更新。

原题链接: <http://oj.leetcode.com/problems/jump-game/> 
这道题是动态规划的题目，所用到的方法跟是在[Maximum Subarray](http://blog.csdn.net/linhuanmars/article/details/21314059)中介绍的套路，用“局部最优和全局最优解法”。我们维护一个到目前为止能跳到的最远距离，以及从当前一步出发能跳到的最远距离。局部最优local=A[i]+i，而全局最优则是global=Math.max(global, local)。递推式出来了，代码就比较容易实现了。因为只需要一次遍历时间复杂度是O(n)，而空间上是O(1)。代码如下： 

**[java]** [view plain](http://blog.csdn.net/linhuanmars/article/details/21354751# "view plain") [copy](http://blog.csdn.net/linhuanmars/article/details/21354751# "copy")

 [![在CODE上查看代码片](resources/BA3ACBF6D7A3420D26DB10207385A617.png)](https://code.csdn.net/snippets/246268 "在CODE上查看代码片")[![派生到我的代码片](resources/02725C4F62B67DC23F2B87E776850078.svg)](https://code.csdn.net/snippets/246268/fork "派生到我的代码片")

1. public boolean canJump(int[] A) {
2. if(A==null || A.length==0)
3. return false;
4. int reach = 0;
5. for(int i=0;i\<=reach&&i\<A.length;i++)
6. {
7. reach = Math.max(A[i]+i,reach);
8. }
9. if(reach\<A.length-1)
10. return false;
11. return true;
12. }

这也是一道比较经典的动态规划的题目，不过不同的切入点可能会得到不同复杂度的算法，比如如果维护的历史信息是某一步是否能够到达，那么每一次需要维护当前变量的时候就需要遍历前面的所有元素，那么总的时间复杂度就会是O(n^2)。所以同样是动态规划，有时候也会有不同的角度，不同效率的解法。这道题目还有一个扩展[Jump Game II](http://blog.csdn.net/linhuanmars/article/details/21356187)，有兴趣的朋友可以看看。

原题链接: <http://oj.leetcode.com/problems/jump-game-ii/> 
这道题是[Jump Game](http://blog.csdn.net/linhuanmars/article/details/21354751)的扩展，区别是这道题不仅要看能不能到达终点，而且要求到达终点的最少步数。其实思路和[Jump Game](http://blog.csdn.net/linhuanmars/article/details/21354751)还是类似的，只是原来的全局最优现在要分成step步最优和step-1步最优（假设当前步数是step）。当走到超过step-1步最远的位置时，说明step-1不能到达当前一步，我们就可以更新步数，将step+1。时间复杂度仍然是O(n)，空间复杂度也是O(1)。代码如下：

**[java]** [view plain](http://blog.csdn.net/linhuanmars/article/details/21356187# "view plain") [copy](http://blog.csdn.net/linhuanmars/article/details/21356187# "copy")

 [![在CODE上查看代码片](resources/BA3ACBF6D7A3420D26DB10207385A617.png)](https://code.csdn.net/snippets/248058 "在CODE上查看代码片")[![派生到我的代码片](resources/02725C4F62B67DC23F2B87E776850078.svg)](https://code.csdn.net/snippets/248058/fork "派生到我的代码片")

1. public int jump(int[] A) {
2. if(A==null || A.length==0)
3. return 0;
4. int lastReach = 0;
5. int reach = 0;
6. int step = 0;
7. for(int i=0;i\<=reach&&i\<A.length;i++)
8. {
9. if(i\>lastReach)
10. {
11. step++;
12. lastReach = reach;
13. }
14. reach = Math.max(reach,A[i]+i);
15. }
16. if(reach\<A.length-1)
17. return 0;
18. return step;
19. }

动态规划是面试中特别是onsite中非常重要的类型，一般面试中模型不会过于复杂，所以大家可以熟悉一下比较经典的几个题，比如[Jump Game](http://blog.csdn.net/linhuanmars/article/details/21354751)，[Maximum Subarray](http://blog.csdn.net/linhuanmars/article/details/21314059)等。