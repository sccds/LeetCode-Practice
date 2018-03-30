### [167\. Two Sum II - Input array is sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

Difficulty: **Easy**



Given an array of integers that is already **_sorted in ascending order_**, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2\. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have _exactly_ one solution and you may not use the _same_ element twice.

**Input:** numbers={2, 7, 11, 15}, target=9  
**Output:** index1=1, index2=2



#### Solution
```python
class Solution:
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        num_dict = dict()
        for i in range(len(numbers)):
            num = numbers[i]
            if target - num in num_dict:
                return [num_dict[target-num]+1, i+1]
            if not num_dict.get(num):
                num_dict[num] = i
        return []
```