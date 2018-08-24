### [28\. Implement strStr()](https://leetcode.com/problems/implement-strstr/description/)

Difficulty: **Easy**


Implement .

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```
**Input:** haystack = "hello", needle = "ll"
**Output:** 2
```

**Example 2:**

```
**Input:** haystack = "aaaaa", needle = "bba"
**Output:** -1
```

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's  and Java's .



#### Solution

Language: **Python3**

```python
class Solution:
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if len(needle) == 0:
            return 0
        if len(haystack) < len(needle):
            return -1
        flag = 1
        for i in range(len(haystack) - len(needle) + 1):
            p = i
            for j in range(len(needle)):
                if haystack[p] != needle[j]:
                    flag = 0
                    p += 1
                    break;
                flag = 1
                p += 1
            if flag == 1:
                return i
        return -1
```