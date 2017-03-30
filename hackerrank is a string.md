解题报告：

此题要求”hackerrank” 按照顺序出现！

审题，看清题目要求！

```python

import sys

def hackerRank(string):
    hack = "hackerrank"
    i = 0
    j = 0
    while i < len(hack) and j < len(string):
        if hack[i] == string[j]:
            i += 1
            j += 1
        else:
            j += 1
    if i == len(hack):
        print "YES"
        
    else:
        print "NO"
    
        

q = int(raw_input().strip())
for a0 in xrange(q):
    s = raw_input().strip()
    # your code goes here
    hackerRank(s)
```