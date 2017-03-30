典型的divide and conquer

找到子树中的最大singlePath 和子树中的最大路径和。

注意如何处理none 节点。

None节点： singlePath 为0 ， 最大路径和不存在 为负无穷。

 \#注意可能存在负数的节点。

 \# singlePath definition: 从子树中某点开始（可能为空）到root点的线长值。

 \# maxPath definition: root节点加上左右singlePath\>= 0 和 左右maxPath 的最大值。注意分析该变量的定义

```python
"""
Definition of TreeNode:
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
"""
class Solution:
    """
    @param root: The root of binary tree.
    @return: An integer
    """
    def maxPathSum(self, root):
        # write your code here
        single,max= self.helper(root)
        return max
        
    def helper(self,root):
        # base case
        if root is None:
            return 0, -sys.maxint
        
        #divide
        ls, lm = self.helper(root.left)
        rs, rm = self.helper(root.right)
        
        #conquer
        #注意可能存在负数的节点。
        # singlePath definition: 从子树中某点开始（可能为空）到root点的线长值。
        # maxPath definition: root节点加上左右singlePath>= 0  和 左右maxPath 的最大值。注意分析该变量的定义
        singlePath = max(0, ls + root.val, rs + root.val)
        maxPath = max(lm, rm, root.val + ls + rs)
        
        return singlePath, maxPath
        
```

