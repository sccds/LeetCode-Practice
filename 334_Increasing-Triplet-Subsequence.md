### [334\. Increasing Triplet Subsequence](https://leetcode.com/problems/increasing-triplet-subsequence/description/)

Difficulty: **Medium**

Given an unsorted array return whether an increasing subsequence of length 3 exists or not in the array.

Formally the function should:  

> Return true if there exists _i, j, k_  
> such that _arr[i]_ < _arr[j]_ < _arr[k]_ given 0 ≤ _i_ < _j_ < _k_ ≤ _n_-1 else return false.

Your algorithm should run in O(_n_) time complexity and O(_1_) space complexity.

**Examples:**  
Given `[1, 2, 3, 4, 5]`,  
return `true`.

Given `[5, 4, 3, 2, 1]`,  
return `false`.


#### Solution
```
class Solution:
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if nums is None or len(nums) < 3:
            return False
        lst = [float("inf")] * 2
        for num in nums:
            if num <= lst[0]:
                lst[0] = num
            elif num <= lst[1]:
                lst[1] = num
            else:
                return True
        return False
```