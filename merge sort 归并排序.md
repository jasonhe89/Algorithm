```python
def sort2(arr):
    temp = [None] * len(arr)
    mergeSort(arr,temp, 0, len(arr) - 1)
    
    
def mergeSort(arr, temp, start, end):
    #end case
    if start >= end:
        return
    mid = (start + end) / 2
    #divide
    mergeSort(arr, temp, start, mid)
    mergeSort(arr, temp,  mid + 1, end)
    #conquer
    merge(arr, temp, start, end)

def merge(arr, temp, left, right):
    leftIndex = left
    mid = (left + right) / 2
    rightIndex = (left + right) / 2 + 1
    tempIndex = left
    while leftIndex <= mid and rightIndex <= right:
        if arr[leftIndex] < arr[rightIndex]:
            temp[tempIndex] = arr[leftIndex]
            tempIndex += 1
            leftIndex += 1
        else:
            temp[tempIndex] = arr[rightIndex]
            tempIndex += 1
            rightIndex += 1
    if leftIndex <= mid:
        while leftIndex <= mid:
            temp[tempIndex] = arr[leftIndex]
            tempIndex += 1
            leftIndex += 1
    else:
        while rightIndex <= right:
            temp[tempIndex] = arr[rightIndex]
            tempIndex += 1
            rightIndex += 1
    for i in range(left, right + 1):
        arr[i] = temp[i]
    print temp
        
l=[3,6,5,4,32,1,8,0,56]
sort2(l)
l
```