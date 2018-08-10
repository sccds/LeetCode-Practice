### [35\. Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)

Difficulty: **Easy**

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

**Example 1:**

```
**Input:** [1,3,5,6], 5
**Output:** 2
```

**Example 2:**

```
**Input:** [1,3,5,6], 2
**Output:** 1
```

**Example 3:**

```
**Input:** [1,3,5,6], 7
**Output:** 4
```

**Example 4:**

```
**Input:** [1,3,5,6], 0
**Output:** 0
```



#### Solution

Language: **Python3**

```python
class Solution:
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if nums is None or len(nums) == 0:
            return -1
        start = 0
        end = len(nums) - 1
        while start + 1 < end:
            mid = start - (start - end) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                start = mid
            elif nums[mid] > target:
                end = mid
        if nums[start] < target <= nums[end]:
            return end
        elif nums[end] < target:
            return end + 1 
        elif nums[start] >= target:
            return start
```