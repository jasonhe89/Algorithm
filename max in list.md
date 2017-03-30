```python
# Enter your code here. Read input from STDIN. Print output to STDOUT
temp = input().split()
size = int(temp[0])
op = int(temp[1])
lst = [0 for _ in range(size)]
for i in range(op):
    Arr = input().split()
    Arr = list(map(int, Arr))
    l = Arr[0]
    r = Arr[1]
    value = Arr[2]
    for i in range(l - 1, r):
        lst[i] += value
print(max(lst))
    
```