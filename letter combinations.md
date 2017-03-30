```python
class Solution:
    def letterCombinations(self, digits):
        dict = {'2' :['a','b','c'],
                '3' :['d','e','f'],
                '4' :['g','h','i'],
                '5' : ['j','k','l'],
                '6' :['m','n','o']
                '7' :['p','q','r','s'],
                '8' :['t','u','v'],
                '9' :['w','x','y','z']
                }
        res = []
        lenght = len(digits)
        if lenght == 0:
            return res
        self.dfs(0,'',res)
        return res
    
    def dfs(self, num, string, res):
        if num == lenght:
            res.append(string)
            return
        for letter in dict[digits[num]]:
            dfs(num+1, string+letter, res)
        
```