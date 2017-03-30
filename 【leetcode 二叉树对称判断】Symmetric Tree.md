<http://blog.csdn.net/u012162613/article/details/41213149>

1、题目
====

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree is symmetric:

        1
       / \
      2   2
     / \ / \
    3  4 4  3

But the following is not:

        1
       / \
      2   2
       \   \
       3    3

<>2、分析
======

判断一棵二叉树本身是否是镜像对称的，这个问题可以转化为：二叉树的左子树与右子树是否是镜像对称的。

问题一经转化，就有一种似曾相识的感觉，上一篇文章刚分析过判断两棵二叉树是否相等的问题，而这道题只不过是把“相等”换为“对称”，方法其实是一样的！

上一篇文章：[【leetcode 二叉树相等判断】Same Tree](http://blog.csdn.net/u012162613/article/details/41212315)

本题的解法同样有递归和迭代两种方法：

（设二叉树左子树为p，右子树为q，p、q均指向左右子树的根）

递归：p和q的值相等，并且p的左子树与q的右子树对称，p的右子树与q的左子树对称

迭代：维护一个栈，方法与上一篇文章中判断二叉树是否相等类似，只不过，我们在将节点入栈的时候，顺序不是 p-\>left , q-\>left ,p-\>right ,q-\>right，而是p-\>left , q-\>right , p-\>right ,q-\>left，为什么？因为我们要判断的是对称，所以p-\>left 对应q-\>right，p-\>right 对应q-\>left，它们的入栈顺序理应如此。

<>3、代码
======

<>\#递归
------

**[cpp]** [view plain](http://blog.csdn.net/u012162613/article/details/41213149# "view plain") [copy](http://blog.csdn.net/u012162613/article/details/41213149# "copy")

1. \<span style="font-size:18px;"\>/\*\*
2. \* Definition for binary tree
3. \* struct TreeNode {
4. \* int val;
5. \* TreeNode \*left;
6. \* TreeNode \*right;
7. \* TreeNode(int x) : val(x), left(NULL), right(NULL) {}
8. \* };
9. \*/
10. class Solution {
11. public:
12. bool isSymmetric(TreeNode \*root) {
13. if(!root) return true; //空树是对称的
14. return symmetric(root-\>left,root-\>right);
15. }
16. private:
17. bool symmetric(TreeNode \*p,TreeNode \*q) /\*判断两棵树是否对称\*/
18. {
19. if(!p && !q) return true; //都是空
20. if(!p || !q) return false; //只有一个空
21. return (p-\>val==q-\>val)&&symmetric(p-\>left,q-\>right) && symmetric(p-\>right,q-\>left);
22. /\*树p和树q对称的条件：p和q的值相同，并且p的左子树与q的右子树对称，p的右子树与q的左子树对称\*/
23. }
24. };\</span\>

<>\#迭代
------

**[cpp]** [view plain](http://blog.csdn.net/u012162613/article/details/41213149# "view plain") [copy](http://blog.csdn.net/u012162613/article/details/41213149# "copy")

1. \<span style="font-size:18px;"\>/\*\*
2. \* Definition for binary tree
3. \* struct TreeNode {
4. \* int val;
5. \* TreeNode \*left;
6. \* TreeNode \*right;
7. \* TreeNode(int x) : val(x), left(NULL), right(NULL) {}
8. \* };
9. \*/
10. class Solution {
11. public:
12. bool isSymmetric(TreeNode \*root) {
13. if(!root) return true; //空树是对称的
14. stack\<TreeNode \*\> s;
15. TreeNode \*p=root-\>left,\*q=root-\>right;
16. s.push(p);
17. s.push(q); //即使是空节点，也是可以push到栈里的，栈并不为空。
18. while(!s.empty())
19. {
20. p=s.top();s.pop();
21. q=s.top();s.pop();
22. 
23. if(!p && !q) continue; //p、q都是空节点
24. if(!p || !q) return false; //有一个为空，不对称
25. if(p-\>val!=q-\>val) return false; //值不相等，不对称
26. 
27. s.push(p-\>left);s.push(q-\>right);
28. s.push(p-\>right);s.push(q-\>left);
29. }
30. return true;
31. }
32. 
33. };\</span\>