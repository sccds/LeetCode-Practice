### [442\. Find All Duplicates in an Array](https://leetcode.com/problems/find-all-duplicates-in-an-array/description/)

Difficulty: **Medium**



Given an array of integers, 1 ≤ a[i] ≤ _n_ (_n_ = size of array), some elements appear **twice** and others appear **once**.

Find all the elements that appear **twice** in this array.

Could you do it without extra space and in O(_n_) runtime?

**Example:**  

```
**Input:**
[4,3,2,7,8,2,3,1]

**Output:**
[2,3]
```



#### Solution

Language: **Python3**

```python
class Solution:
    def findDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        if nums is None or len(nums) == 0:
            return list()
        res = list()
        for i in range(len(nums)):
            idx = abs(nums[i]) - 1
            if nums[idx] < 0:
                res.append(idx + 1)
            nums[idx] = -nums[idx]
        return res
```