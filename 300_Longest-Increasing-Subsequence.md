### [300\. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/description/)

Difficulty: **Medium**

Given an unsorted array of integers, find the length of longest increasing subsequence.

For example,  
Given `[10, 9, 2, 5, 3, 7, 101, 18]`,  
The longest increasing subsequence is `[2, 3, 7, 101]`, therefore the length is `4`. Note that there may be more than one LIS combination, it is only necessary for you to return the length.

Your algorithm should run in O(_n<sup>2</sup>_) complexity.

**Follow up:** Could you improve it to O(_n_ log _n_) time complexity?

#### 解题思路
- f[i] 表示前i个数中，以第i个数结尾的 LIS
- f[i] max(1, A[j]) A[j] <= A[i]

#### Solution
```
class Solution:
    def lengthOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        f = [0 for _ in range(len(nums))]
        maxx = 0
        for i in range(len(nums)):
            f[i] = 1
            for j in range(i):
                if nums[j] < nums[i]:
                    f[i] = f[i] if f[i] > f[j] + 1 else f[j] + 1
            if f[i] > maxx:
                maxx = f[i]
        return maxx
                    
```
