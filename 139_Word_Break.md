### [139\. Word Break](https://leetcode.com/problems/word-break/description/)

Difficulty: **Medium**

Given a **non-empty** string _s_ and a dictionary _wordDict_ containing a list of **non-empty** words, determine if _s_ can be segmented into a space-separated sequence of one or more dictionary words.

**Note:**

*   The same word in the dictionary may be reused multiple times in the segmentation.
*   You may assume the dictionary does not contain duplicate words.

**Example 1:**

```
**Input:** s = "leetcode", wordDict = ["leet", "code"]
**Output:** true
**Explanation:** Return true because `"leetcode"` can be segmented as `"leet code"`.
```

**Example 2:**

```
**Input:** s = "applepenapple", wordDict = ["apple", "pen"]
**Output:** true
**Explanation:** Return true because `"`applepenapple`"` can be segmented as `"`apple pen apple`"`.
             Note that you are allowed to reuse a dictionary word.
```

**Example 3:**

```
**Input:** s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
**Output:** false
```

#### 解题思路
```
f[i] 表示前i个字符能否被dict完美划分

function
f[i] = 只要有这样一个 j, 使 f[j] == true && j < i && j + 1 ~ i 是一个词典中的词   , 则 f[i] = true
否则 f[i] = false

f[i] = OR(f[j], j < i && j + 1 ~ i 是 dict 里的一个单词)

init:
f[0] = true

answer:
f[s.length]

note:  
切分位置的枚举 => 单词长度枚举  
O(NL), N: 字符串长度， L: dict里面最长的单词的长度
```


#### Solution
```python
class Solution:
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: bool
        """
        if len(wordDict) == 0:
            return len(s) == 0
        max_len = max(map(len, wordDict))
        n = len(s)
        f = [False] * (n+1)
        f[0] = True
        j = 1
        for i in range(1, len(s)+1):
            for j in range(1, min(i, max_len) + 1):
                if not f[i - j]:
                    continue
                word = s[i - j : i]
                if word in wordDict:
                    f[i] = True
                    break
        return f[len(s)]
            
​
```

