### [151\. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description/)

Difficulty: **Medium**



Given an input string, reverse the string word by word.

**Example:  **

```
**Input:** "`the sky is blue`",
**Output: **"`blue is sky the`".
```

**Note:**

*   A word is defined as a sequence of non-space characters.
*   Input string may contain leading or trailing spaces. However, your reversed string should not contain leading or trailing spaces.
*   You need to reduce multiple spaces between two words to a single space in the reversed string.

**Follow up: **For C programmers, try to solve it _in-place_ in _O_(1) space.



#### Solution

Language: **Python**

```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        import re
        ls = re.sub(' +', ' ', s.strip()).split(" ")
        print(ls)
        return " ".join(self.reverse(ls, 0, len(ls)-1))
    
    def reverse(self, lst, start, end):
        while start < end:
            lst[start], lst[end] = lst[end], lst[start]
            start += 1
            end -= 1
        return lst
```