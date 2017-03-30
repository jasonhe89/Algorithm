利用dfs 找到给定数组中是否能找出一组数 使得其和为target

```python
def dfs(index, nums, sumSoFar, target):
    if index == len(nums): #we have made all the choices 
        #已做出全部决定，下标移动到数组的nil
        return sumSoFar == target
    if dfs(index+1, nums, sumSoFar + nums[index], target):
        return True
    if dfs(index+1, nums, sumSoFar , target):
        return True
    return False
    
dfs(0,[1,2,3,4,5],0,15)
```