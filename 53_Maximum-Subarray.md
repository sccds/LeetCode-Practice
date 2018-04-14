### [53\. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/)

Difficulty: **Easy**



Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,  
the contiguous subarray `[4,-1,2,1]` has the largest sum = `6`.

**More practice:**

If you have figured out the O(_n_) solution, try coding another solution using the divide and conquer approach, which is more subtle.


#### 解题思路
遍历数组，如果 (sum + num) 比 num 本身小，从这个数字开始；如果 (sum + num) 比 num 大，继续


#### Solution
```
class Solution:
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        summ = 0
        maxx = float("-inf")
        for num in nums:
            summ = max(num, summ + num)
            maxx = max(summ, maxx)
        return maxx
                
```