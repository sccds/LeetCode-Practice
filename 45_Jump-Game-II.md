### [45\. Jump Game II](https://leetcode.com/problems/jump-game-ii/description/)

Difficulty: **Hard**

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Your goal is to reach the last index in the minimum number of jumps.

**Example:**

```
**Input:** [2,3,1,1,4]
**Output:** 2
**Explanation:** The minimum number of jumps to reach the last index is 2.
    Jump 1 step from index 0 to 1, then 3 steps to the last index.```

**Note:**

You can assume that you can always reach the last index.
```

#### 解题思路
动态规划：
- state: f[i] 代表跳到这个位置最少需要几步
- function: f[i] = min(f[j] + 1, j < i && j能够跳到i)
- init: f[0] = 0
- answer: f[n-1]

#### Solution
```python
class Solution:
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        steps = [float("inf") for _ in range(len(nums))]
        steps[0] = 0
        for i in range(1, len(nums)):
            for j in range(i):
                if steps[j] != float("inf") and j + nums[j] >= i:
                    steps[i] = min(steps[i], steps[j] + 1)
        return steps[len(nums) - 1]
```


贪心：
```python
class Solution:
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums is None or len(nums) == 0:
            return -1
        start, end, jumps = 0, 0, 0
        while end < len(nums) - 1:
            jumps += 1
            farthest = end
            for i in range(start, end+1):
                if i + nums[i] > farthest:
                    farthest = i + nums[i]
            start = end + 1
            end = farthest
        return jumps
```


