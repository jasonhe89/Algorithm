[https://aaronice.gitbooks.io/lintcode/content/data\_structure/kth\_smallest\_number\_in\_sorted\_matrix.html](https://aaronice.gitbooks.io/lintcode/content/data_structure/kth_smallest_number_in_sorted_matrix.html)

=======================================================================================================================================================================================================================

Kth Smallest Number in Sorted Matrix
====================================

Find the kth smallest number in a row and column sorted matrix.

Example

Given k = 4 and a matrix:

```
[
  [1 ,5 ,7],
  [3 ,7 ,8],
  [4 ,8 ,9],
]

```

return `5`

Challenge

O(k log n), n is the maximal number in width and height.

Tags

`Heap` `Priority Queue` `Matrix`

Related Problems

Hard Kth Smallest Sum In Two Sorted Arrays

Medium Kth Largest Element

Analysis
--------

寻找第k小的数，可以联想到转化为数组后排序，不过这样的时间复杂度较高：O(n^2 log n^2) + O(k).

进一步，换种思路，考虑到堆（Heap）的特性，可以建立一个Min Heap，然后poll k次，得到第k个最小数字。不过这样的复杂度仍然较高。

考虑到问题中矩阵本身的特点：排过序，那么可以进一步优化算法。

```
[1 ,5 ,7],
[3 ,7 ,8],
[4 ,8 ,9],

```

因为行row和列column都已排序，那么matrix中最小的数字无疑是左上角的那一个，坐标表示也就是(0, 0)。寻找第2小的数字，也就需要在(0, 1), (1, 0)中得出；以此类推第3小的数字，也就要在(0, 1), (1, 0), (2, 0), (1, 1), (0, 2)中寻找。

在一个数字集合中寻找最大（Max）或者最小值（Min），很快可以联想到用Heap，在Java中的实现是Priority Queue，它的pop，push操作均为O(logn)，而top操作，得到堆顶仅需O(1)。

从左上(0, 0)位置开始往右/下方遍历，使用一个Hashmap记录visit过的坐标，把候选的数字以及其坐标放入一个大小为k的heap中（只把未曾visit过的坐标放入heap），并且每次放入前弹出掉（poll）堆顶元素，这样最多会添加（push）2k个元素。时间复杂度是O(klog2k)，也就是说在矩阵自身特征的条件上优化，可以达到常数时间的复杂度，空间复杂度也为O(k)，即存储k个候选数字的Priority Queue （Heap）。

Solution
--------

```
class Number {
    public int x, y, val;
    public Number(int x, int y, int val) {
        this.x = x;
        this.y = y;
        this.val = val;
    }
}

class NumberComparator implements Comparator\<Number\> {
    public int compare(Number a, Number b) {
        return a.val - b.val;
    }
}

public class Solution {
    private boolean isValid(int x, int y, int[][] matrix, boolean[][] visited) {
        if (x < matrix.length && y < matrix[x].length && !visited[x][y]) {
            return true;
        }
        return false;
    }

    int[] dx = new int[] {0, 1};
    int[] dy = new int[] {1, 0};

    /\*\* \* @param matrix: a matrix of integers \* @param k: an integer \* @return: the kth smallest number in the matrix \*/
    public int kthSmallest(int[][] matrix, int k) {
        // Validate input
        if (matrix == null || matrix.length == 0) {
            return -1;
        }
        if (matrix.length * matrix[0].length < k) {
            return -1;
        }

        // Define min heap
        PriorityQueue<Number> heap = new PriorityQueue<Number>(k, new NumberComparator());

        heap.add(new Number(0, 0, matrix[0][0]));

        // Define visited matrix
        boolean[][] visited = new boolean[matrix.length][matrix[0].length];

        visited[0][0] = true;    

        for (int i = 0; i < k - 1; i++) {
            Number smallest = heap.poll();

            for (int j = 0; j < 2; j++) {
                // Next coordinates
                int nx = smallest.x + dx[j];
                int ny = smallest.y + dy[j];

                if (isValid(nx, ny, matrix, visited)) {
                    visited[nx][ny] = true;
                    heap.add(new Number(nx, ny, matrix[nx][ny]));
                }
            }
        }

        return heap.peek().val;
    }
}
```