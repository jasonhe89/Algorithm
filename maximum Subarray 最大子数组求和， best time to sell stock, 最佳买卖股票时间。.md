这个题目有三种思想：

1 动态规划－－－不难

2 PreSum ， MaxSumSofar， minPreSumSoFar.

 重点理解： MaxSumSofar 当前index 时， 算出的最大subarry 和。

 minPreSumSoFar. 当前index 时， 在该index 前面的最小前N项和， preSum[x]

3 贪心：

for (int i = 0; i \< nums.size(); ++i) {

f = max(f + nums[i], nums[i]);

result = max(result, f);

}

**陷阱，此题无法通过找preSum的最大值和最小值来求得 答案**

**因为最小值可能在最大值后面，所以必须在遍历preSum数组的时候，计算MaxSoFar， 直到结束才能知道Max 是什么！**

**
**

**这题要记住需要使用两个量，在建立preSum（前n项和） 数组之后， 利用**

**＊＊ leastPreSum 当前最小的前n项和， **

**＊＊maxSoFar 前n 项中 最大的subarry sum （子数组和）**

**
**

**遍历preSumArray 即可。**

def maxSubArray(self, nums):

 \#pre sum

 preSum = []

 preSum.append(0)

 for i in range(len(nums)):

 preSum.append(preSum[i] + nums[i])

 leastPreSum = sys.maxint

 maxSoFar = -(sys.maxint - 1)

 for s in preSum:

 ＃ 更新当前最大的subarray Sum

 if s - leastPreSum \> maxSoFar:

 maxSoFar = s - leastPreSum

 ＃更新当前的最小前N项和

 if leastPreSum \> s:

 leastPreSum = s

 return maxSoFar

-------------------

**\*\*Dynamic programming \*\***

**动态规划的思想： **

** 状态表示： endHere[i] —— 到 i 时，到第n－1项 连续子数组的和。**

** 状态转移： 比较endHere[i] 和0 的大小。**

** if endHere[i] \< 0:**

** endHere[i+1] = nums[i+1]**

** else:**

** endhere[i+1] = nums[i+1] + endHere[i] **

def maxSubArray(self, nums):

 \#dynamic programming

 endHere = []

 endHere.append(0)

 for i in range(len(nums)):

 if endHere[i] \< 0:

 endHere.append(nums[i])

 else:

 endHere.append(nums[i] + endHere[i])

 endHere.pop(0)

** return max(endHere)**

arry [-2 2 -3 4 -1 2 1 -5 3]

presum [-2 0 -3 1 0 2 1 -4 -1]

这题还有一种方法Prefix Sum，在九章答案里有。就是累积求从0到当前i的总和sum，然后sum减去从0开始到当前i之前某一位j的最小sum值，然后用sum减去这个最小sum值就是这一段总的最大值。建议把这个方法一块加上吧.....

int maxSubArray(vector\<int\>& nums) {

int result = INT\_MIN, f = 0;

for (int i = 0; i \< nums.size(); ++i) {

f = max(f + nums[i], nums[i]);

result = max(result, f);

}

return result;

}

**上面这段算法本质是贪心。**