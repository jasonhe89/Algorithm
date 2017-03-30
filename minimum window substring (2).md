```python
def minWindow(self, source, target):
    S, T = source, target
    d, dt = {}, dict.fromkeys(T,0)
    for c in T:
        d[c] = d.get(c,0) + 1
    pi, pj, count = 0, 0, 0
    ans = ""
    while pj < len(S):
        char = S[pj]
        if char in dt:
            if dt[char] < d[char]:
                count += 1
            dt[char] += 1
        
        if count == len(T):
            while pi < pj:
                slowChar = S[pi]
                if slowChar in dt:
                    if dt[slowChar] == d[slowChar]:
                        break
                    dt[slowChar] -= 1
                pi += 1
                
            if ans== '' or pj - pi < len(ans):
                ans = S[pi:pj+1]
            dt[S[pi]] -= 1
            pi += 1
            count -=1
        pi += 1
        
    return ans
```