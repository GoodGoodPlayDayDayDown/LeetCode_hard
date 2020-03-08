# 题目名称：最短回文串

## 题目链接：https://leetcode-cn.com/problems/shortest-palindrome/


## 题解：

给定一个字符串，在前面添加最少的字符，使得该字符串变成回文串。

显然我们应该从后面选择一定长度的子串，逆序后进行添加，这个长度应该递增，从而保证最小。

但其实这种算法很不好，因为不断地重复，而没有用到前后之间的关系，进而会达到O（n^2）的复杂度。

那么更好的解法？一种是KMP算法的应用，一种是Manacher算法的应用。

Manacher算法的解释可以参见LeetCode第五题寻找最大回文子串，https://leetcode-cn.com/problems/longest-palindromic-substring/solution/zhong-xin-kuo-san-dong-tai-gui-hua-by-liweiwei1419/  。也就是，使用这种算法找到了最大回文子串，我们可以将扫描中心，即回文子串的中心往前定一些，保证最大回文子串是从第一个字符开始的，这样一来剩下的就是我们要翻转放到前面的部分。

KMP算法可以参见https://blog.csdn.net/dark_cy/article/details/88698736  ， 将其应用可以参见题解https://leetcode-cn.com/problems/shortest-palindrome/solution/c-li-yong-kmpsuan-fa-xiang-xi-tui-dao-zhuan-hua-gu/ 。

我只能评价一句，都是神仙算法，将复杂度降低为线性，充分利用相互关系而不重复运算。