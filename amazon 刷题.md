最新面经：

帮朋友发的[店面](http://www.meetqun.com/forum-36-1.html)[面经](http://www.meetqun.com/forum-36-1.html)，问了一些[算法](http://www.meetqun.com/forum-36-1.html)基本知识，比如hashtable, 时间复杂度的分析，最后的code 是leetcode Two Sum

我是博士在读，内推得到亚马逊的电面。12月16号面的。一共大概55分钟，前面35分钟聊了一下科研项目什么的，然后开始一道coding题，题目是LC上面的max points on a line的变种。原题是求最大有多少个点，我的题目是把这些点，以及这一条线都要返回出来。我听到以后直接蒙掉，之后有一点点思路，但是没有写完。在写的过程中，面试官估计没有太看懂我的代码，就打断了我一下下，问了一下我的思路，我乘机和他说了一下，他全程没有评论与暗示，就是简单的附和，比如“ok"一类的。

BST find the second largest number

实现泛型queue

Part 1：
是一个美国的女人。全程态度挺好的，没什么口音。上来还是问简历里的一个Project，遇到什么困难，怎么解决之类的。
Part2：
基础知识部分：问了什么是继承，虚类和接口有啥区别，还问了HashMap的内部实现，处理冲突的问题。。
Part3：
两道题：
1：Two Sum：不多说了。。
2：判断一个树是不是回文树。（妥妥跪了）我默认为就是结构对称的了。。。然后就用了中序遍历加两个指针来判断。
实际上应该用递归来判断是不是回文树。.鏈枃鍘熷垱鑷�1point3acres璁哄潧
Part4：
问了问她一些问题。。

问了下简历上的内容，然后问了下SQL PYTHON 使用情况，然后让描述一个处理Data 解决问题的情景。

楼主你好 我12月onsite了ad组挂了。电面Java基础 OOD概念题 coding是LRU

一面有点不记得了，有一题是问在Browser输入域名，整个反应过程。刷过雅虎面经的应该都懂得这道题。browser cache-\>DNS-\>Http packge。系统设计问的是MP3播放器。
今天二面，1\. LinkedList从排 1-\>last 1-\> 2-\> last 2-\>... 比如，1-\>2-\>3-\>4-\>5，变成1-\>5-\>2-\>4-\>3。方法是拆分，后半部Reverse，重组。
2，系统设计设计ParkingLot。最问，用什么数据结构存储，可以快速找到停车位。HashMap\<Type, HashSet\<Integer\>\>，就是把车型\<Key\>跟availabe的车位\<value\>存起来。
感觉二面是会挂，三哥不太满意的样子，因为小错误很多。但是人很Nice，加了10多分钟，让我把第二题面完。从以前面大公司的经验是会挂。.鏈枃鍘熷垱鑷�1point3acres璁哄潧
以下是在地里前辈基础上总结的题。 鏉ユ簮涓€浜�.涓夊垎鍦拌鍧�.

1\. 家具：have a furniture class, some child classes like table, chair, etc.
they want to extend the class hierarchy, as there are wood table, steel
table, wood chair, steel chair, and so on.
2\. design a parking lot.
3\. design a zoo.
4\. design a file system.
这几个设计大概注意点什么，用到什么design pattern了？（刚刚go over了一下
amazon的design的题，发现这几个题出
现不止一次，当然还有其他的题，不过从这个里希望得到些灵感。）
谢谢各位了。

### leetcode: letter combination

无向图距离

数组排序

单词权数

largest k element

#### Longest Consecutive Sequence

<http://www.geeksforgeeks.org/find-index-0-replaced-1-get-longest-continuous-sequence-1s-binary-array/>

Hello, I am really sorry for replying you this late. I have been looking forward to this interview opportunity for a long time and am really excited to get the invitation. With my great passion of joining Amazon, I already started to prepare for the interview. Hope we can meet at Amazon in the future! 

I attached my available time below. Also, my phone number is 702-6820990\. Please contact me if there were any questions. I'll be waiting for your reply. 

Again, thank you so much and have a good day!



lz上周面的，面完第三天收到offer. 很感谢前辈分享面经，才让我面试过程中基本都按照自己准备的套路来，虽然有一些小插曲，但总体还算顺利。 先贴几个我觉得不错的面经，其实把这些面经好好看完全足够了。（地里有一些老的群面的面经，应该不用看了） 很多同学求资料，我觉得倒不如静下心来把已有的面经研究清楚。我知道一开始这些面经看上去都不太清晰，可是花几天时间慢慢看就懂了（因为项目本身也挺庞大）。 Amazon Onsite C++ Simplified Skeleton Code + 资料包 作者需要拥有至少50积分以显示此链接. 最推荐的是这个。有代码，好好把代码研究清楚。真正用到的类代码里基本都有。 Amazon 补一个群面过经验 作者需要拥有至少50积分以显示此链接. 这个提到好多技术之外的。其实我觉得挺重要，因为面试官应该也就是面试的时候看看你的代码，之后应该不会再看了。对于第二轮project，就只有30min+15min跟面试官交流的时间，一定要好好把握！ 划一下重点：清楚自己的思路，言之有理。比如说，我第二个 milestone2 就直接用的 greedy（当然也建议先从简单的方法入手），而且我当时跟面试官说了原因一二三，面试官好像挺开心赶紧记了下来。 同时，写注释非常重要。我花了挺长时间写注释的，当时把每个题目的实现方法一二三，每个方法的复杂度是什么，我自己做了哪个，为什么，等等都写下来了。我两轮面试都是一开始就照着我的comments说，两轮面试官看到我写的，都说 I like your comments. 我觉得主要的好处是，把comments写下来之后你的思路会非常清晰，跟面试官有点紧张的情况下也能说清楚，是在不行就照着comments读嘛。 注意 corner case. 比如 milestone1，如果得到的shippingcost列表为空，就不用加到结果里面了。 亚马逊-群面-一点进阶的idea 作者需要拥有至少50积分以显示此链接. 然后如果把前面都看了，两个milestone都看懂了，可以看看这个帖子提升的方法 还有个最近发的帖子，讲到了 milestone2 backtracking 的写法，感觉很厉害： 新鲜亚麻onsite面经 作者需要拥有至少50积分以显示此链接. （还有累了可以看一下这篇文学大作lol 西城漫记 作者需要拥有至少50积分以显示此链接.） 第二部分讲讲 Python. 第一是可以提前熟悉一下 Windows VS 的环境。 第二是要熟悉 Python class 的一些知识。比如要知道 @property 这个decorator。 class Order(object): def \_\_init\_\_(self, quantity): self.\_quantity = quantity @property def quantity(self): return self.\_quantity 如果要获得 \_quantity 这个属性的值，直接 Instance.quantity 就好（没有括号）。 第三是，当时我第一个 milestone 想用 dictionary 来做，但是报错，应该是 Region类的 instance 不能 hashable. 大家可以提前准备一下遇到这问题怎么解决。 我们当天面试的里面挺多同学也都收到offer了。大家好好准备，千万不要觉得 project 看起来很复杂说到时临场发挥，准备得越充分当然是越好的。加油！

链接: <https://instant.1point3acres.com/thread/212499>
来源: 一亩三分地