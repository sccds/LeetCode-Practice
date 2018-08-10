### [34\. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)

Difficulty: **Medium**


Given an array of integers `nums` sorted in ascending order, find the starting and ending position of a given `target` value.

Your algorithm's runtime complexity must be in the order of _O_(log _n_).

If the target is not found in the array, return `[-1, -1]`.

**Example 1:**

```
**Input:** nums = [`5,7,7,8,8,10]`, target = 8
**Output:** [3,4]```

**Example 2:**

```
**Input:** nums = [`5,7,7,8,8,10]`, target = 6
**Output:** [-1,-1]```



#### Solution

Language: **Python3**

```python
class Solution:
    def searchRange(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        if nums is None or len(nums) == 0:
            return [-1, -1]
        if len(nums) == 1 and nums[0] == target:
            return [0, 0]
        elif len(nums) == 1 and nums[0] != target:
            return [-1, -1]
        
        left_bound = -1
        right_bound = -1
        
        # find left bound
        start = 0
        end = len(nums) - 1
        while start + 1 < end:
            mid = start - (start - end) // 2
            if nums[mid] >= target:
                end = mid
            elif nums[mid] < target:
                start = mid
        if nums[start] == target:
            left_bound = start
        elif nums[end] == target:
            left_bound = end
        else:
            left_bound = -1
            
        # find right bound
        start = 0
        end = len(nums) - 1
        while start + 1 < end:
            mid = start - (start - end) // 2
            if nums[mid] <= target:
                start = mid
            elif nums[mid] > target:
                end = mid
        if nums[end] == target:
            right_bound = end
        elif nums[start] == target:
            right_bound = start
​
        return [left_bound, right_bound]
```