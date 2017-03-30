

```java
import copy
class Solution:
    """
    @param {TreeNode} root The root of the binary tree.
    @param {TreeNode} A and {TreeNode} B two nodes
    @return Return the LCA of the two nodes.
    """ 
    def lowestCommonAncestor3(self, root, A, B):
        # write your code here
       
        Alst = self.findParentLst(root, A)
        #print self.Alst
        Blst = self.findParentLst(root, B)
        print [x.val for x in Alst]
        print [x.val for x in Blst]
        a = [i for i in Alst if i in Blst]
        if a !=[]:
            return a[0]
        else:
            return None
        
    def findParentLst(self, root, target):
        #print lst
        if root is None:
            return []
        if root is target:
            return [target]
        
        left = self.findParentLst(root.left, target)
        right = self.findParentLst(root.right, target)
        if left != []:
            return left + [root] 
        if right != []:
            return right + [root] 
        return []
        
        
```