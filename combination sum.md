```python
class Solution:
    # @param candidates, a list of integers
    # @param target, integer
    # @return a list of lists of integers
    def combinationSum(self, candidates, target):
        # write your code here
        candidates = list(set(candidates))
        candidates.sort()
        self.result = []
        self.dfs(candidates, target, 0, [])
        return self.result
        
    def dfs(self,candidates, target, start, valueList):
        length = len(candidates)
        
        if target == 0:
            return self.result.append(valueList)
        
        for i in range(start,length):
            if target < candidates[i]:
                return
            self.dfs(candidates, target - candidates[i], i, valueList + [candidates[i]])
```