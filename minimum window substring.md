分析下面为何不行

```python
class Solution:
    """
    @param source: A string
    @param target: A string
    @return: A string denote the minimum window
             Return "" if there is no such a string
    """
    def minWindow(self, source, target):
        # write your code here
        T = {}
        for i in range(len(target)):
            T[target[i]] = T.get(target[i], 0 ) + 1
        print T

        length = sys.maxint
        j = 0
        for i in range(len(source)):
            while j < len(source):
                #判断是否已经满足覆盖
                if source[j] in T:
                    T[source[j]] -= 1
                #未满足覆盖j 继续向前走
                if self.checkCover(T) is False:
                    j += 1
                else:
                    length = min(length, j - i + 1)
                    break
                #如果满足了就break
            print T
            print source[i:j+1]
            if source[i] in T:
                T[source[i]] += 1
                
                
        return length
```

公司要出套Java面试题, 写到算法处理字符串这段，想起MWS算法，比较有代表性且数据结构取巧。
现在把解题思路再梳理一把。

> 给定一个字符串S和T，在S中找到一个最小的子串包含T中的所有字符，时间复杂度为O(n)。
> Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).
> 
> 举例,
> S = "ADOBECODEBANC"
> T = "ABC"
> 最小子串是"BANC".

这里有几个点需要说明下：

时间复杂度是O(n)
==========

其中n是字符串S的长度，因为每个字符在维护窗口的过程中不会被访问多于两次。

空间复杂度则是O(1)
===========

也就是代码中T的长度。

数据结构选择
======

记录字母出现次数的数据结构有采用哈希Map的也有采用数组的，这里介绍一下数组的用法，因为它用了比较取巧的方式。
大小写字母的ASCII码不大于128，这样array['A']=3指A出现3次，array['B']=1指B出现了一次，以此类推，不能用常规意义上的定义array[0]=3表示A出现3次，这样就多了一层映射！故而数组的长度设置为128即可存放所有的字母。明白了么？

算法思想：
=====

1. 首先预处理T，用一个128长 (示例代码用了256) 的整数数组srcHash存储里面每个目标字符出现的个数
2. 然后处理原串S，也用一个128长的整数数组destHash记录原串字符出现的个数。给定两个指针start和end，作为最小窗口的左右边界。具体实现看下代码一目了然。

```
    public class Solution {
        public String minWindow(String S, String T) {
            int[] srcHash = new int[255];
            // 记录目标字符串每个字母出现次数
            for(int i = 0; i < T.length(); i++){
                srcHash[T.charAt(i)]++;
            }
            int start = 0,i= 0;
            // 用于记录窗口内每个字母出现次数 
            int[] destHash = new int[255];
            int found = 0;
            int begin = -1, end = S.length(), minLength = S.length();
            for(start = i = 0; i < S.length(); i++){
                // 每来一个字符给它的出现次数加1
                destHash[S.charAt(i)]++;
                // 如果加1后这个字符的数量不超过目标串中该字符的数量，则找到了一个匹配字符
                if(destHash[S.charAt(i)] <= srcHash[S.charAt(i)]) found++;
                // 如果找到的匹配字符数等于目标串长度，说明找到了一个符合要求的子串 
                if(found == T.length()){
                    // 将开头没用的都跳过，没用是指该字符出现次数超过了目标串中出现的次数，并把它们出现次数都减1
                    while(start < i && destHash[S.charAt(start)] > srcHash[S.charAt(start)]){
                        destHash[S.charAt(start)]--;
                        start++;
                    }
                    // 这时候start指向该子串开头的字母，判断该子串长度
                    if(i - start < minLength){
                        minLength = i - start;
                        begin = start;
                        end = i;
                    }
                    // 把开头的这个匹配字符跳过，并将匹配字符数减1
                    destHash[S.charAt(start)]--;
                    found--;
                    // 子串起始位置加1，我们开始看下一个子串了
                    start++;
                }
            }
            // 如果begin没有修改过，返回空
            return begin == -1 ? "" : S.substring(begin,end + 1);
        }
    }
```

### 加深理解：

解题思路其实就是通过双指针维持一个Window，窗口右指针向右扩张用来找到包含子串为目的，窗口左指针向右收缩以使子串最小。
典型的滑动窗口方法的实现。

```python
class Solution:
    def minWindow(self, source, target):
        if (target == ""):
            return ""
        S , T = source, target
        #d 字典保存的是每个字符需要出现的次数
        # dt保存的是滑动窗口中目标字符出现的次数
        d, dt = {}, dict.fromkeys(T, 0)
        for c in T: d[c] = d.get(c, 0) + 1
        # j fast, i slow pointer
        # cont 来统计窗口中有效字符个数
        pi, pj, cont = 0, 0, 0
        if (source =="" or target ==""):
            return ""
        ans = ""
        while pj < len(S):
            if S[pj] in dt:
                if dt[S[pj]] < d[S[pj]]:
                    cont += 1
                dt[S[pj]] += 1;
            if cont == len(T):
                while pi < pj:
                    if S[pi] in dt:
                        if dt[S[pi]] == d[S[pi]]:
                            break;
                        dt[S[pi]] -= 1;
                    pi+= 1
                if ans == '' or pj - pi < len(ans):
                    ans = S[pi:pj+1]
                dt[S[pi]] -= 1
                pi += 1
                cont -= 1
            pj += 1
        return ans
s = Solution()
s.minWindow('ADOBECODEBANC', 'ABC')
```

本质上利用双指针，字典记录，有效字符数状态 来优化程序运行。

有效字符数可以被一个函数 －－ 窗口已包含所有要求字符 －－ 来替换

