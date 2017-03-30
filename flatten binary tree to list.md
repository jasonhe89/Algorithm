```python
def class Solution:
    lastNode = None
    def flatten(self,root):
        if root is None:
            return
        if lastNone != None:
            lastNode.left = null
            lastNode.right = root
        lastNode = root
        right = root.right
        flatten(root.left)
        flatten(right)
```