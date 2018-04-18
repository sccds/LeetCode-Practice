### [646\. Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/description/)

Difficulty: **Medium**


You are given `n` pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair `(c, d)` can follow another pair `(a, b)` if and only if `b < c`. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order.

**Example 1:**  

```
**Input:** [[1,2], [2,3], [3,4]]
**Output:** 2
**Explanation:** The longest chain is [1,2] -> [3,4]
```

**Note:**  

1.  The number of given pairs will be in the range [1, 1000].

#### 解题思路
- 先对列表排序
- 然后用类似 LIS 的方法，只是判断条件不一样


#### Solution
```
class Solution:
    def findLongestChain(self, pairs):
        """
        :type pairs: List[List[int]]
        :rtype: int
        """
        f = [0 for _ in range(len(pairs))]
        maxx = 0
        pairs = sorted(pairs, key=lambda x: x[0])
        for i in range(len(pairs)):
            f[i] = 1
            for j in range(i):
                if pairs[j][1] < pairs[i][0]:
                    f[i] = f[i] if f[i] > f[j] + 1 else f[j] + 1
            if f[i] > maxx:
                maxx = f[i]
        return maxx    
```