### [168\. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/description/)

Difficulty: **Easy**


Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB
```


#### Solution
```
class Solution:
    def convertToTitle(self, n):
        """
        :type n: int
        :rtype: str
        """
        if n == 0:
            return ""
        return self.convertToTitle((n - 1) // 26) + chr((n - 1) % 26 + ord('A'))
                                   
```