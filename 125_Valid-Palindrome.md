### [125\. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)

Difficulty: **Easy**

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,  
`"A man, a plan, a canal: Panama"` is a palindrome.  
`"race a car"` is _not_ a palindrome.

**Note:**  
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

#### Solution
```
class Solution:
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        import re
        s = re.sub('[^a-zA-Z0-9]', '', s).lower()
        start = 0
        end = len(s) - 1
        while start <= end:
            if s[start] != s[end]:
                return False
            start += 1
            end -= 1
        return True
        
```