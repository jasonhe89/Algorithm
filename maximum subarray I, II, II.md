[Maximum Subarray / Best Time To Buy And Sell Stock 与 prefixNum](http://www.cnblogs.com/ireneyanglan/p/4890515.html)
====================================================================================================================

这两个系列的题目其实是同一套题，可以互相转换。

首先我们定义一个数组: prefixSum （前序和数组）

Given nums: [1, 2, -2, 3]

prefixSum: [0, 1, 3, 1, 4 ]

现在我们发现对prefixSum做Best Time To Buy And Sell Stock和对nums做Maximum Subarray，结果相同。

接下来我们就利用prefixSum解这两个系列的题目。

[Maximum Subarray](http://www.lintcode.com/en/problem/maximum-subarray/ "lintcode1")

### Question

Given an array of integers, find a contiguous subarray which has the largest sum.

**Example**

Given the array `[−2,2,−3,4,−1,2,1,−5,3]`, the contiguous subarray `[4,−1,2,1]` has the largest sum = `6`.

**Note**

The subarray should contain at least one number.

### Solution

Sum of subarray i to j can be calculated by **prefixSum[j] - prefixSum[i - 1]**.

Two variables, so we hope to make prefixSum[i - 1] minimum, while prefixSum[j] maximum.

Example

nums 1 1 1 -4 6 1 -5

prefixSum 0 1 2 3 -1 5 6 1

min 0 0 0 0 0 -1 -1 -1

max sub 0 1 2 3 3 6 7 7

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

     1 public class Solution {  2     public int maxSubArray(ArrayList<Integer> nums) {  3         int length = nums.size();  4         // Construct prefixSum
     5         int[] prefixSum = new int[length + 1];  6         prefixSum[0] = 0;  7         for (int i = 0; i < length; i++)  8             prefixSum[i + 1] = prefixSum[i] + nums.get(i);  9         // Traverse prefixSum 10         // min: minimum number before i 11         // result: maximum subarray from 0 to i
    12         int min = 0; 13         int result = Integer.MIN\_VALUE; 14         for (int i = 0; i < length; i++) { 15             int current = prefixSum[i + 1]; 16             result = Math.max(result, current - min); 17             min = Math.min(current, min); 18  } 19         return result; 20  } 21 }

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

Similar: [Minimum Subarray](http://www.lintcode.com/en/problem/minimum-subarray/ "lintcode4")

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

     1 public class Solution {  2     public int minSubArray(ArrayList<Integer> nums) {  3         int length = nums.size();  4         int sum = 0;  5         int maxSum = 0;  6         int minSum = Integer.MAX\_VALUE;  7         for (int i = 0; i < length; i++) {  8             sum += nums.get(i);  9             minSum = Math.min((sum - maxSum), minSum); 10             maxSum = Math.max(maxSum, sum); 11  } 12         return minSum; 13  } 14 }

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

[Maximum Subarray II](http://www.lintcode.com/en/problem/maximum-subarray-ii/ "lintcode2")

### Question

Given an array of integers, find **two** **non-overlapping** subarrays which have the largest sum.

The number in each subarray should be contiguous.

Return the largest sum.

**Example**

For given **[1, 3, -1, 2, -1, 2]**, the two subarrays are **[1, 3]** and **[2, -1, 2]** or **[1, 3, -1, 2]** and** [2]**, they both have the largest sum **7**.

**Note**

The subarray should contain at least one number

### Solution

The problem can be translated as

Finding a strip line in the array, to make the sum of its max **left** subarray and max **right** subarray is max.

We can traverse the input array and list all possible value of the strip line, and then calculated its left max and right max. The time complexity is O(n2). But this still wastes a lot of time for duplicated calculation.

Actually we can just travers twice and get result. Time complexity is O(n).

maxLeft is max subarray on strip line's left side (inclusive). maxRight is max subarray on strip line's right side (inclusive).

nums 1 1 1 -4 6 1 -5

prefixSumLeft 0 1 2 3 -1 5 6 1

minL 0 0 0 0 0 -1 -1 -1

**maxLeft** 1 2 3 3 6 7 7

prefixSumRight 1 0 -1 -2 2 -4 -5 0

minR -5 -5 -5 -5 -5 -5 0 0

**maxRight** 7 7 7 7 7 1 0

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

     1 public class Solution {  2     
     3     public int maxTwoSubArrays(ArrayList<Integer> nums) {  4         int length = nums.size();  5         int[] left = new int[length];  6         int[] right = new int[length];  7         int sum = 0;  8         int minSum = 0;  9         int maxSum = Integer.MIN\_VALUE; 10         // left
    11         for (int i = 0; i < length; i++) { 12             sum += nums.get(i); 13             maxSum = Math.max(maxSum, (sum - minSum)); 14             left[i] = maxSum; 15             minSum = Math.min(minSum, sum); 16  } 17         // right
    18         sum = 0; 19         minSum = 0; 20         maxSum = Integer.MIN\_VALUE; 21         for (int i = length - 1; i >= 0; i--) { 22             sum += nums.get(i); 23             maxSum = Math.max(maxSum, (sum - minSum)); 24             right[i] = maxSum; 25             minSum = Math.min(minSum, sum); 26  } 27         
    28         int result = Integer.MIN\_VALUE; 29         for (int i = 0; i < length - 1; i++) 30             result = Math.max(result, left[i] + right[i + 1]); 31         return result; 32  } 33 }

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

[Maximum Subarray III](http://www.lintcode.com/en/problem/maximum-subarray-iii/ "lintcode3")

### Question

Given an array of integers and a number k, find k `non-overlapping` subarrays which have the largest sum.

The number in each subarray should be **contiguous**.

Return the largest sum.

**Example**

Given `[-1,4,-2,3,-2,3]`, `k=2`, return `8`

**Note**

The subarray should contain at least one number

### Solution