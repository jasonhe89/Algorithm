`# A Naive recursive Python program to fin minimum number`

`# operations to convert str1 to str2`

`def` `editDistance(str1, str2, m , n):`

`    ``# If first string is empty, the only option is to`

`    ``# insert all characters of second string into first`

`    ``if` `m``=``=``0``:`

`         ``return` `n`

`    ``# If second string is empty, the only option is to`

`    ``# remove all characters of first string`

`    ``if` `n``=``=``0``:`

`        ``return` `m`

`    ``# If last characters of two strings are same, nothing`

`    ``# much to do. Ignore last characters and get count for`

`    ``# remaining strings.`

`    ``if` `str1[m``-``1``]``=``=``str2[n``-``1``]:`

`        ``return` `editDistance(str1,str2,m``-``1``,n``-``1``)`

`    ``# If last characters are not same, consider all three`

`    ``# operations on last character of first string, recursively`

`    ``# compute minimum cost for all three operations and take`

`    ``# minimum of three values.`

`    ``return` `1` `+` `min``(editDistance(str1, str2, m, n``-``1``),    ``# Insert`

`                   ``editDistance(str1, str2, m``-``1``, n),    ``# Remove`

`                   ``editDistance(str1, str2, m``-``1``, n``-``1``)    ``# Replace`

`                   ``)`

`# Driver program to test the above function`

`str1 ``=` `"sunday"`

`str2 ``=` `"saturday"`

`print` `editDistance(str1, str2, ``len``(str1), ``len``(str2))`

<http://www.geeksforgeeks.org/dynamic-programming-set-5-edit-distance/>

![](resources/E90212019D905B100429A651390856C0.jpg)

Given two words word1 and word2, find the minimum number of steps required to convert word1 to word2\. (each operation is counted as 1 step.)

You have the following 3 operations permitted on a word:

a) Insert a character

b) Delete a character

c) Replace a character

SOLUTION 1:

REF:
<http://www.cnblogs.com/etcow/archive/2012/08/30/2662985.html>
<http://www.cnblogs.com/etcow/archive/2012/08/30/2662985.html>
<http://blog.csdn.net/fightforyourdream/article/details/13169573>
<http://www.cnblogs.com/TenosDoIt/p/3465316.html>

相当经典的一道递归题目，而且难度级别为4.

*
*这是一个典型的2维DP.
定义D[i][j] 为string1 前i个字符串到 string2的前j个字符串的转化的最小步。
1\. 初始化： D[0][0] = 0; 2个为空 不需要转
2\. D[i][0] = D[i - 1][0] + 1\. 就是需要多删除1个字符
3\. D[0][j] = D[0][j - 1] + 1\. 就是转完后需要添加1个字符

D[i][j] 的递推公式：
我们来考虑最后一步的操作：
从上一个状态到D[i][j]，最后一步只有三种可能：
添加，删除，替换（如果相等就不需要替换）

a、给word1插入一个和word2最后的字母相同的字母，这时word1和word2的最后一个字母就一样了，此时编辑距离等于1（插入操作） + 插入前的word1到word2去掉最后一个字母后的编辑距离
D[i][j - 1] + 1
例子： 从ab --\> cd
我们可以计算从 ab --\> c 的距离，也就是 D[i][j - 1]，最后再在尾部加上d

b、删除word1的最后一个字母，此时编辑距离等于1（删除操作） + word1去掉最后一个字母到word2的编辑距离
D[i - 1][j] + 1
例子： 从ab --\> cd
我们计算从 a --\> cd 的距离，再删除b, 也就是 D[i - 1][j] + 1

c 、把word1的最后一个字母替换成word2的最后一个字母，此时编辑距离等于 1（替换操作） + word1和word2去掉最后一个字母的编辑距离。
这里有2种情况，如果最后一个字符是相同的，即是：D[i - 1][j - 1]，因为根本不需要替换，否则需要替换，就是
D[i - 1][j - 1] + 1

然后取三种情况下的最小距离

现在来证明一下，当最后一个字符相同时，D[i][j] = D[i - 1][j - 1]，这里只要证明D[i - 1][j -1] \<=D[i ][j - 1]+1即可。
反证法：
假设：D[i - 1][j -1] \> D[i ][j - 1]+1
推论：如果我们要把i-1字符串变换为j - 1,
 我们可以通过先在str1加上一个字符，得到带前i个字符的str1 , 然后再执行D[i][j -1]
 D[i][j - 1] + 1 也可以推出 i , j 字符串的转换 也就是说
 推出：D[i - 1][j - 1]不是i - 1--\> j - 1转换的最小值
 推论与题设相矛盾，所以得证。

基于以上证明，当最后一个字符相同时，我们其实可以直接让D[i][j] = D[i - 1][j - 1].*

*

例子： "ababd" -\> "ccabab"

 先初始化matrix如下。意思是，比如"\_" -\> "cca" = 3 操作是插入'c','c','a'，共3步。 "abab" -\> "+ "\_" 删除'a','b','a','b'，共4 步。

 \_ababd\_012345c1     c2     a3     b4     a5     b6     

 然后按照注释里的方法填满表格，返回最后一个数字（最佳解）

 \_ababd\_012345c112345c222345a323234b432323a543233b654323

![](resources/405B18B4B6584AE338E0F6ECAF736533.gif)

[![复制代码](resources/51E409B11AA51C150090697429A953ED.gif)]( "复制代码")

     1 public class Solution {  2     public int minDistance(String word1, String word2) {  3         if (word1 == null || word2 == null) {  4             return 0;  5  }  6         
     7         int len1 = word1.length();  8         int len2 = word2.length();  9         
    10         int[][] D = new int[len1 + 1][len2 + 1]; 11         
    12         for (int i = 0; i <= len1; i++) { 13             for (int j = 0; j <= len2; j++) { 14                 if (i == 0) { 15                     D[i][j] = j; 16                 } else if (j == 0) { 17                     D[i][j] = i; 18                 } else { 19                     if (word1.charAt(i - 1) == word2.charAt(j - 1)) { 20                         D[i][j] = D[i - 1][j - 1]; 21                     } else { 22                         D[i][j] = Math.min(D[i - 1][j - 1], D[i][j - 1]); 23                         D[i][j] = Math.min(D[i][j], D[i - 1][j]); 24                         D[i][j]++; 25  } 26  } 27  } 28  } 29         
    30         return D[len1][len2]; 31  } 32 }