```python

def find(x, y):
    if x > y:
        return 1;
    ans = pow(Arr[x-1], find(x+1,y))
    return ans

N = int(input().strip())
Arr = input().split()
Arr = list(map(int, Arr))
Q = int(input().strip())

for i in range(Q):
    xy = input().split()
    xy = list(map(int, xy))
    #print(xy)
    result = find(xy[0], xy[1])
    if result % 2 == 0:
        print("Even")
    else:
        print("Odd")
```