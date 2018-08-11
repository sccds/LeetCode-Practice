### [186\. Reverse Words in a String II](https://leetcode.com/problems/reverse-words-in-a-string-ii/description/)

Difficulty: **Medium**


Given an input string, reverse the string word by word. 

**Example:**

```
**Input:** ["t","h","e"," ","s","k","y"," ","i","s"," ","b","l","u","e"]
**Output:** ["b","l","u","e"," ","i","s"," ","s","k","y"," ","t","h","e"]```
```

**Note: **

*   A word is defined as a sequence of non-space characters.
*   The input string does not contain leading or trailing spaces.
*   The words are always separated by a single space.

**Follow up: **Could you do it _in-place_ without allocating extra space?

**思路：**
```
Input:  ["t","h","e"," ","s","k","y"," ","i","s"," ","b","l","u","e"]
middle: [e, h, t, " ", y, k, s, " ", s, i, " ", e, u, l, b]
reverse
Output: ["b","l","u","e"," ","i","s"," ","s","k","y"," ","t","h","e"]
```

#### Solution

Language: **Python**

```python
class Solution(object):
    def reverseWords(self, str):
        """
        :type str: List[str]
        :rtype: void Do not return anything, modify str in-place instead.
        """
        left = 0
        for i in range(len(str)+1):
            if i == len(str) or str[i] == ' ':
                self.reverse(str, left, i - 1)
                left = i + 1
        self.reverse(str, 0, len(str)-1)
        
    def reverse(self, lst, start, end):
        while start < end:
            lst[start], lst[end] = lst[end], lst[start]
            start += 1
            end -= 1
        return lst
```