**Example**

For numbers `[1,2,2]` the unique permutations are:

```
[
  [1,2,2],
  [2,1,2],
  [2,2,1]
]
```

思路：还是运用permutaiton的模版——backtrack 的基本框架。

但是这一题如果没有mark已经访问过的元素（即在permutation I 的答案下去重），会输出如下结果

    [[1, 1, 1],
     [1, 1, 2],
     [1, 2, 1],
     [1, 2, 2],
     [2, 1, 1],
     [2, 1, 2],
     [2, 2, 1],
     [2, 2, 2]]

    **造成这一答案的原因是没有记录下某个元素是否被使用过。**

    因此permutation II的定义可以理解为：将[1,2,2]中的每个元素都取一遍，取的顺序无所谓，但是最后答案要去重。

```python
class Solution:
    def permuteUnique(self,nums):
        if len(nums) == 0:
            return [[]]
        results = []
        nums.sort()
        lst = []
        visited = [0] *len(nums)    #记录某个元素是否访问过。
        self.helper(results,lst, visited,nums)
        return results
    def helper(self,results, lst, visited, nums):
        if len(lst) == len(nums):
            if lst in results:    # 重复元素不能算答案。
                return
            results.append(list(lst))
            return
        for i in range(len(nums)):
            if visited[i] == 1:
                continue
            visited[i] = 1
            lst.append(nums[i])   
            self.helper(results,lst,visited,nums)
            lst.pop()
            visited[i] = 0
        return
```

**Permutation I**

给定一个数字列表，返回其所有可能的排列。

**样例**

给出一个列表`[1,2,3]`，其全排列为：

```
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```

#####  注意事项

你可以假设没有重复数字。

思路: permutation I的定义可以理解为：将[1,2,3]中的每个元素都取一遍，取的顺序无所谓,因为没有重复元素，所以我们很happy, code比较简单。

```python
#该模版更好
class Solution:
    def permute(self,nums):
        if len(nums) == 0:
            return [[]]
        results = []
        nums.sort()
        lst = []
        visited = [0] *len(nums)    #记录某个元素是否访问过。
        self.helper(results,lst, visited,nums)
        return results
    def helper(self,results, lst, visited, nums):
        if len(lst) == len(nums):
            #if lst in results:    # 重复元素不能算答案。
            #    return
            results.append(list(lst))
            return
        for i in range(len(nums)):
            if visited[i] == 1:
                continue
            visited[i] = 1
            lst.append(nums[i])     #将当前元放入到结果lst的这个位置中
            self.helper(results,lst,visited,nums) #把剩下的位置填满
            lst.pop()     #这个位置我们不放当前元素，放别的啦
            visited[i] = 0
        return
```

下面的模版一般

```python
class Solution:
    """
    @param nums: A list of Integers.
    @return: A list of permutations.
    """
    def permute(self, nums):
        # write your code here
        result = []
        self.helper(nums,[], result)
        return result
        
    def helper(self, nums, lst, result):
        if len(lst) == len(nums):
            result.append(list(lst))
            return 
        for i in range(len(nums)):
            if nums[i] in lst:
                continue
            lst.append(nums[i])
            self.helper(nums, lst, result)
            lst.remove(nums[i])
```

```python

```