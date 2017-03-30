这题的思路就是找到target node 之后， 找到target node 的右子树中的最左节点。如果没有右子树，那么就返回 之前向左走之前的node, 该node 是第一大于target node 的节点！

```clojure
class Solution(object):
    """
    @param root <TreeNode>: The root of the BST.
    @param p <TreeNode>: You need find the successor node of p.
    @return <TreeNode>: Successor of p.
    """
    def inorderSuccessor(self, root, p):
        # write your code here
        if root is None or p is None:
            return None
        
        curt = root
        succ = None
        
        while curt != p and curt != None:
            if curt.val < p.val: #current node val is smaller than targer val, we should go right
                curt = curt.right
            elif curt.val > p.val: #current node val is bigger than target val, we should go left
                succ = curt
                curt = curt.left
            if curt is None:
                return None
        
        if curt.right is None:
            return succ
        curt = curt.right
        while curt.left is not None:
            curt = curt.left
        return curt
```