思路解析：

我们默认第一个元素已排序，从下表为1（第二个元素）开始，在已经排序的数组中找到插入位置。 

假设前 i-1 个元素已经排序，eg 2,3 插入1

2 3 1 ==\> 2 3 3 =\> 2 2 3=\> 1 2 3.

2 3 \_ ==\> 2 \_ 3 =\> \_ 2 3 =\> 1 2 3

1 3 2 =\> 1 3 \_ =\> 1 \_ 3 =\> 1 2 3.

利用j 从后向前扫描已经排序的数数组，

```python
selection sort
```
def insertionSort(lst):
    for i in range(1,len(lst)):
        j = i
        temp = lst[i]
        while j > 0 and lst[j-1] > temp:
            lst[j] = lst[j-1]
            j -= 1
        lst[j] = temp
		
```
```

仔细体会两者不同，分析优劣。

```python
class Solution:
    # @param {int[]} A an integer array
    # @return nothing
    def sortIntegers(self, A):
        for i in range(1, len(A)):
            j = i - 1
            temp = A[i]
            while j >= 0 and temp < A[j]:
                A[j+1] = A[j]
                j -= 1
            A[j+1] = temp
```

Selection sort

```python
class Solution:
    # @param {int[]} A an integer array
    # @return nothing
    def sortIntegers(self, A):
        
        for i in range(len(A) - 1):
            minIndex = i
            for j in range(i+1, len(A)):
                if A[minIndex] > A[j]:
                    minIndex = j
            A[i], A[minIndex] = A[minIndex], A[i]
```

bubble sort

```python
def bubbleSort(lst):
    for i in range(len(lst)-1, -1, -1):
        for j in range(0,i):
            if lst[j] > lst[j+1]:
                lst[j],lst[j+1] = lst[j+1],lst[j]
l = [3,2,1,4,5]
bubbleSort(l)
l
```

```python
def bubbleSort(alist):
    for passnum in range(len(alist)-1,0,-1):
        for i in range(passnum):
            if alist[i]>alist[i+1]:
                temp = alist[i]
                alist[i] = alist[i+1]
                alist[i+1] = temp

alist = [54,26,93,17,77,31,44,55,20]
bubbleSort(alist)
print(alist)
```