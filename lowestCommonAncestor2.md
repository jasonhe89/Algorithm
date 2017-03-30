下面的代码之所以跑不出来，写不对，就是逻辑太复杂了，当逻辑复杂的时候，需要求助于数据结构！！！

```java
class Solution:
    """
    @param root: The root of the binary search tree.
    @param A and B: two nodes in a Binary.
    @return: Return the least common ancestor(LCA) of the two nodes.
    """ 
    def lowestCommonAncestor(self, root, A, B):
        # write your code here
        t, l = self.helper(root, A,B)
        return l
        
    def helper(self,root, A, B):
        #base case
        if root == None:
            return False, None
            
        if root == A or root == B:
            return False, root
        #divide 
        leftTrue , leftnode = self.helper(root.left, A, B) 
        rightTrue , rightnode =self.helper(root.right, A, B)
        
        #conquer
        if (leftnode, rightnode) == (A,B) or (leftnode, rightnode) == (B,A):
            return True, root
            
        if leftTrue == True:
            return leftTrue, leftnode
        if rightTrue == True:
            return rightTrue, rightnode
            
        if leftnode == A or leftnode == B:
            return False, leftnode
        if rightnode == A or rightnode == B:
            return False, rightnode
```