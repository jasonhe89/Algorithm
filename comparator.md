```
def compare(x,y): if x == y: return 0 elif x == 0: return 1 elif y == 0: return -1 else: return cmp(x,y) sorted(myarr, cmp=lambda x,y: compare(x,y), key=lambda x:x['rank'])
```

1) Sort using sorted() function or sort()

```
## Initial Array
array = [8, 2, 9, 0, 1, 2, 5];
## General sorting
array.sort()
print array

## Another approach
## using function
print sorted(array)
```

2) Now sorting using custom comparator function.

```
## custom sort
def comparator(x, y):
    return x-y

## Initial Array
array = [8, 2, 9, 0, 1, 2, 5];
array.sort(comparator)
print array
```

This the very basic of a comparator function. Its just take two objects as parameter, and compare, after that it just return like xy.

3) Now put some logic inside the comparator function for your own purpose.

```
## custom sort
def comparator(x, y):
    ## Just a condition for example,
    ## you can add as many you need.
    if(x % 2):
        return x
    return x-y

## Initial Array
array = [8, 2, 9, 0, 1, 2, 5];
array.sort(comparator)
print array
```