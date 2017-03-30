```clojure
class Solution:
    # @param A: Given an integer array
    # @return: void
    def heapify(self, A):
        # write your code here
        n = len(A) / 2
        while n >= 0 :
            self.minHeapify(A, n)
            n -= 1
    
    def minHeapify(self, A, i):
        l = i * 2 + 1
        r = i * 2 + 2
        small = i
        if l < len(A) and A[i] > A[l]:
            small = l
        if r < len(A) and A[small] > A[r]:
            small = r
        if small != i:
            A[small] , A[i] = A[i], A[small]
            self.minHeapify(A, small)
```

这道题是hepify 一个given array。

用的方法是找heap中的最小值 和root 比较。 如果root 不是最小，那么要swap 最小值和root. 因为子heap 的结构破坏了，所以我们要对子堆递归heapify。