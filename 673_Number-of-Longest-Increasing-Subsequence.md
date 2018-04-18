### [673\. Number of Longest Increasing Subsequence](https://leetcode.com/problems/number-of-longest-increasing-subsequence/description/)

Difficulty: **Medium**

Given an unsorted array of integers, find the number of longest increasing subsequence.

**Example 1:**  

```
**Input:** [1,3,5,4,7]
**Output:** 2
**Explanation:** The two longest increasing subsequence are [1, 3, 4, 7] and [1, 3, 5, 7].
```

**Example 2:**  

```
**Input:** [2,2,2,2,2]
**Output:** 5
**Explanation:** The length of longest continuous increasing subsequence is 1, and there are 5 subsequences' length is 1, so output 5.
```

**Note:** Length of the given array will be not exceed 2000 and the answer is guaranteed to be fit in 32-bit signed int.


#### 解题思路
- 在 LIS 的基础上，增加另一个状态列表，记录数量

```
[1,3,5,4,7]

1 0 [1, 2, 1, 1, 1] [1, 1, 1, 1, 1]
2 0 [1, 2, 2, 1, 1] [1, 1, 1, 1, 1]
2 1 [1, 2, 3, 1, 1] [1, 1, 1, 1, 1]
3 0 [1, 2, 3, 2, 1] [1, 1, 1, 1, 1]
3 1 [1, 2, 3, 3, 1] [1, 1, 1, 1, 1]
3 2 [1, 2, 3, 3, 1] [1, 1, 1, 1, 1]
4 0 [1, 2, 3, 3, 2] [1, 1, 1, 1, 1]
4 1 [1, 2, 3, 3, 3] [1, 1, 1, 1, 1]
4 2 [1, 2, 3, 3, 4] [1, 1, 1, 1, 1]
4 3 [1, 2, 3, 3, 4] [1, 1, 1, 1, 2]
```


#### Solution
```
class Solution:
    def findNumberOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        f = [1 for _ in range(len(nums))]
        ans = [1 for _ in range(len(nums))]
        for i in range(len(nums)):
            for j in range(i):
                if nums[j] < nums[i]:
                    if f[j] + 1 > f[i]:
                        f[i] = f[j] + 1
                        ans[i] = ans[j]
                    elif f[j] + 1 == f[i]:
                        ans[i] += ans[j]
                #print(i, j, f, ans)
        return sum(y for x, y in zip(f, ans) if x == max(f))
```

