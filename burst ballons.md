\begin
 x + y = z
 x + y = z
\end

\begin{align}
对于气球问题，我们假设有 1-n 个气球， 每个气球的分数为 S_{i}, i \in {1..n}\\
我们的目标是求出打爆 1-n， 使得 这n个气球得到的最大分数。\\
对于任意过程中，假设我们打爆 ith 个气球,所得分数为 S_{i-1} * S_{i} * S_{i+1}\\
定义以下函数来帮助我们求的最大分数。
假设我们打爆kth 气球，所得分数为S_{head - 1} * S_{k} * S_{end + 1}
\\best(head,end) = best(head, k-1) + best(k+1 , end) + S_{head - 1} * S_{k} * S_{end + 1}\\
k \in {head..end}\\

case n = 1 => score = S_{i}
\end{align}
\begin{align}
\\ 
\\f(x) &= x^2\\
f'(x) &= 2x\\
F(x) &= \int f(x)dx\\
F(x) &= \frac{1}{3}x^3
\end{align}

我们在一个架子上有一排酒打算卖掉，价格排列为 eg. p = 1, 4, 2, 3

每年只能从架子左边或者右边取一瓶酒。

酒的价格为 year \* pi

求最大售价是多少。

from pandas import \*

p = [1,4,2,3]

N = len(p)

cache = [[None] \* len(p) for \_ in range(len(p))]

def profit(begin, end):

 if begin \> end:

 return 0

 if cache[begin][end] != None:

 return cache[begin][end]

 year = N - (end - begin + 1) +1

 a = profit(begin+1, end) + year \* p[begin]

 b = profit(begin, end-1) + year \* p[end]

 cache[begin][end] = max(a,b)

 print "a is " + str(a) + " b is " + str(b)

 print "year" + str(year)

 print DataFrame(cache)

 return cache[begin][end]

x = profit(0, len(p) - 1)

print x