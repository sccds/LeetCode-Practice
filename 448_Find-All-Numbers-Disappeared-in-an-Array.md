### [448\. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)

Difficulty: **Easy**


Given an array of integers where 1 ≤ a[i] ≤ _n_ (_n_ = size of array), some elements appear twice and others appear once.

Find all the elements of [1, _n_] inclusive that do not appear in this array.

Could you do it without extra space and in O(_n_) runtime? You may assume the returned list does not count as extra space.

**Example:**

```
**Input:**
[4,3,2,7,8,2,3,1]

**Output:**
[5,6]
```

**思路:**  
相应index位置的元素，取反。最后整理一下大于0的元素index


#### Solution

Language: **Python3**

```python
class Solution:
    def findDisappearedNumbers(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        if nums is None or len(nums) == 0 :
            return list()
        res = list()
        for i in range(len(nums)):
            idx = abs(nums[i])
            if nums[idx-1] > 0:
                nums[idx-1] = -nums[idx-1]
            else:
                nums[idx-1] = nums[idx-1]
        for i in range(len(nums)):
            if nums[i] > 0:
                res.append(i + 1)
        return res
                
```