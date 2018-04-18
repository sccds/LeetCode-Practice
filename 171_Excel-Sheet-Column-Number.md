### [171\. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/description/)

Difficulty: **Easy**


Related to question

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```


#### Solution
```
class Solution:
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        summ = 0
        for ch in list(s):
            tmp = ord(ch) - ord('A') + 1
            summ = 26 * summ + tmp
        return summ
```