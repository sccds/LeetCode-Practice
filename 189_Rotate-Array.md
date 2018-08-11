### [189\. Rotate Array](https://leetcode.com/problems/rotate-array/description/)

Difficulty: **Easy**



Given an array, rotate the array to the right by _k_ steps, where _k_ is non-negative.

**Example 1:**

```
**Input:** `[1,2,3,4,5,6,7]` and _k_ = 3
**Output:** `[5,6,7,1,2,3,4]`
**Explanation:**
rotate 1 steps to the right: `[7,1,2,3,4,5,6]`
rotate 2 steps to the right: `[6,7,1,2,3,4,5]` rotate 3 steps to the right: `[5,6,7,1,2,3,4]`
```

**Example 2:**

```
**Input:** `[-1,-100,3,99]` and _k_ = 2
**Output:** [3,99,-1,-100]
**Explanation:** 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

**Note:**

*   Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
*   Could you do it in-place with O(1) extra space?

**思路：**
三步翻转法：
```
- [1, 2, 3, 4, 5, 6, 7]
- [4, 3, 2, 1, 5, 6, 7]
- [4, 3, 2, 1, 7, 6, 5]
- [5, 6, 7, 1, 2, 3, 4]
```


#### Solution

Language: **Python3**

```python
class Solution:
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        if k >= len(nums):
            k = k - len(nums)
        if nums is None or len(nums) == 0 or len(nums) == 1 or k == 0:
            return 
        self.reverse(nums, 0, len(nums) - k - 1)
        self.reverse(nums, len(nums) - k, len(nums) - 1)
        self.reverse(nums, 0, len(nums) - 1)
        
    def reverse(self, nums, start, end):
        while start < end:
            nums[start], nums[end] = nums[end], nums[start]
            start += 1
            end -= 1
        return nums
            
```