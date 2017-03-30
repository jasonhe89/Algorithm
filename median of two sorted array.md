[https://aaronice.gitbooks.io/lintcode/content/array/median\_of\_two\_sorted\_arrays.html](https://aaronice.gitbooks.io/lintcode/content/array/median_of_two_sorted_arrays.html)

Median of two Sorted Arrays
===========================

<http://www.lintcode.com/en/problem/median-of-two-sorted-arrays/>

Question
--------

> There are two sorted arrays A and B of size m and n respectively. Find the median of the two sorted arrays.
> 
> Example
> 
> Given A=[1,2,3,4,5,6] and B=[2,3,4,5], the median is 3.5.
> 
> Given A=[1,2,3] and B=[4,5], the median is 3.

Analysis
--------

参考[九章中的解释](http://www.jiuzhang.com/solutions/median-of-two-sorted-arrays/)：

对于一个长度为n的已排序数列a，若n为奇数，中位数为a[n / 2 + 1], 若n为偶数，则中位数(a[n / 2] + a[n / 2 + 1]) / 2; 如果我们可以在两个数列中求出第K小的元素，便可以解决该问题; 不妨设数列A元素个数为n，数列B元素个数为m，各自升序排序，求第k小元素; 取A[k / 2] B[k / 2] 比较; 如果 A[k / 2] \> B[k / 2] 那么，所求的元素必然不在B的前k / 2个元素中(证明反证法); 反之，必然不在A的前k / 2个元素中，于是我们可以将A或B数列的前k / 2元素删去，求剩下两个数列的; k - k / 2小元素，于是得到了数据规模变小的同类问题，递归解决; 如果 k / 2 大于某数列个数，所求元素必然不在另一数列的前k / 2个元素中，同上操作就好。

相关： [Data Stream Median](http://www.lintcode.com/en/problem/data-stream-median/)

Solution
--------

```

class Solution {
    /\*\* \* @param A: An integer array. \* @param B: An integer array. \* @return: a double whose format is \*.5 or \*.0 \*/
    public double findMedianSortedArrays(int[] A, int[] B) {
        int totalLength = A.length + B.length;
        if (totalLength % 2 == 1) {
            return findKth(A, 0, B, 0, totalLength / 2 + 1);
        }
        return (findKth(A, 0, B, 0, totalLength / 2) + findKth(A, 0, B, 0, totalLength / 2 + 1)) / 2.0;
    }

    public int findKth(int[] A, int A\_start, int[] B, int B\_start, int k) {
        if (A_start >= A.length) {
            return B[B_start + k - 1];
        }
        if (B_start >= B.length) {
            return A[A_start + k - 1];
        }

        if (k == 1) {
            return Math.min(A[A_start], B[B_start]);
        }

        int A_key = A_start + k / 2 - 1 < A.length
                ? A[A_start + k / 2 - 1]
                : Integer.MAX_VALUE;
        int B_key = B_start + k / 2 - 1 < B.length
                ? B[B_start + k / 2 - 1]
                : Integer.MAX_VALUE;

        if (A_key < B_key) {
            return findKth(A, A_start + k / 2, B, B_start, k - k / 2);
        } else {
            return findKth(A, A_start, B, B_start + k / 2, k - k / 2);
        }

    }
}
```

