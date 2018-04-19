### [132\. Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/description/)

Difficulty: **Hard**


Given a string _s_, partition _s_ such that every substring of the partition is a palindrome.

Return the minimum cuts needed for a palindrome partitioning of _s_.

For example, given _s_ = `"aab"`,  
Return `1` since the palindrome partitioning `["aa","b"]` could be produced using 1 cut.


#### 解题思路
- state: f[i] 前i个字符组成的子字符串需要最少几次 cut (最少能被分割为多少个字符串-1)
- function: f[i] = min (f[j+1], j < i && j + 1 ~ i 这一段也是个回文串)
- init: f[i] = i - 1 (f[0] = -1)
- answer: f[s.length()]

- 子问题，判断 回文串  
    + s[i] == s[j] && isPali(i+1 ~ j-1)
    + 需要事先定义好list，否则复杂度 O(n^3)

#### Solution
```
class Solution:
    def minCut(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s is None or len(s) == 0:
            return 0
        
        # preperation
        is_palindrome_lst = self.get_is_palindrome(s)
        
        # init
        n = len(s)
        f = [i - 1 for i in range(n+1)]
        f[0] = 0
        
        # DP
        for i in range(1, n+1):
            f[i] = float("inf")
            for j in range(i):
                if is_palindrome_lst[j][i-1]:
                    f[i] = min(f[i], f[j] + 1)
        
        return f[n] - 1
​
        
    def get_is_palindrome(self, s):
        is_palindrome_lst = [[False for _ in range(len(s))] for _ in range(len(s))]
        
        # 先把长度为1，2的初始化，从长度为3的开始
        for i in range(len(s)):
            is_palindrome_lst[i][i] = True
        for i in range(len(s)-1):
            is_palindrome_lst[i][i + 1] = (s[i] == s[i + 1])
        
        # 从坐标差为2的开始
        for length in range(2, len(s)):
            start = 0
            while start + length < len(s):
                is_palindrome_lst[start][start + length] = is_palindrome_lst[start + 1][start + length - 1] and s[start] == s[start + length]
                start += 1
        return is_palindrome_lst
        
```


