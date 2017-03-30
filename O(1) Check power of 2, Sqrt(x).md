思路： 利用移位运算

01 \<\< 1 === 10

1 \<\<1 ==== 2

```python
def checkPowerOf2(n):
    ans = 1 
    for i in xrange(31):
        if ans == n:
            return True
        ans = ans << 1
    return False
```

SQRT(X)

```python
class Solution:
    def sqrt(self, x):
        start, end = 0, x
        while start + 1 < end:
            mid = start + (end - start) / 2
            if mid * mid < x:
                start = mid
            else:
                end = mid
        if end * end <= x :
            return end
        else:
            return start

            
```