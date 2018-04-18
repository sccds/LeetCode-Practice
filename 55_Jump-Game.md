### [55\. Jump Game](https://leetcode.com/problems/jump-game/description/)

Difficulty: **Medium**



Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

For example:  
A = `[2,3,1,1,4]`, return `true`.

A = `[3,2,1,0,4]`, return `false`.


#### 解题思路
方法一：DP
- state: f[i] 代表能否从起点跳到第i个位置
- function: f[i] = or (f[j], j < i && j + A[j] >= i (j 能跳到 i))
- init: f[0] = true
- answer: f[n-1]

#### Solution => **Time Limit Exceeded**
```python
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        can = [False for _ in range(len(nums))]
        can[0] = True
        for i in range(1, len(nums)):
            for j in range(i):
                if can[j] and j + nums[j] >= i:
                    can[i] = True
                    break
        return can[len(nums) - 1]
```


方法二：Greedy

```python
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if nums is None or len(nums) == 0:
            return False
        farest = nums[0]
        for i in range(1, len(nums)):
            if i <= farest and i + nums[i] >= farest:
                farest = i + nums[i]
        return farest >= len(nums) - 1
```


