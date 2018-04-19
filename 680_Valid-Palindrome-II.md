### [680\. Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/description/)

Difficulty: **Easy**


Given a non-empty string `s`, you may delete **at most** one character. Judge whether you can make it a palindrome.

**Example 1:**  

```
**Input:** "aba"
**Output:** True
```

**Example 2:**  

```
**Input:** "abca"
**Output:** True
**Explanation:** You could delete the character 'c'.
```

**Note:**  

1.  The string will only contain lowercase characters a-z. The maximum length of the string is 50000.


#### Solution
```
class Solution:
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        left, right = 0, len(s)-1
        skipped = False
        while left <= right:
            if s[left] == s[right]:
                left += 1
                right -= 1
            else:
                if skipped:
                    return False
                else:
                    skipped = True
                    
                    # try left move
                    tmp_left, tmp_right = left + 1, right
                    while tmp_left < tmp_right:
                        if s[tmp_left] != s[tmp_right]:
                            break
                        tmp_left += 1
                        tmp_right -= 1
                        if tmp_left >= tmp_right:
                            return True
                    
                    # if left move doesn't work, try move right
                    right -= 1
        return True
                    
                
```