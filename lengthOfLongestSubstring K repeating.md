```python
class Solution:
    # @param s : A string
    # @return : An integer
    def lengthOfLongestSubstringKDistinct(self, s, k):
        # write your code here
        if s is None or len(s) == 0:
            return 0
        
        T = {}
        j = 0
        length = 1
        for i in range(len(s)):
            while j < len(s) and ( T.get(s[j], 0 ) + 1) <= k:
                length = max(length, j - i + 1)
                T[s[j]] =  T.get(s[j], 0 ) + 1
                j += 1
            T[s[i]] -= 1
        
        return length
        
```