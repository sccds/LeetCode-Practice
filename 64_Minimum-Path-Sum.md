### [64\. Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/description/)

Difficulty: **Medium**



Given a _m_ x _n_ grid filled with non-negative numbers, find a path from top left to bottom right which _minimizes_ the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

**Example 1:**  

```
[[1,3,1],
 [1,5,1],
 [4,2,1]]
```

Given the above grid map, return `7`. Because the path 1→3→1→1→1 minimizes the sum.

#### Solution
```python
class Solution:
    def minPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        m = len(grid)
        n = len(grid[0])
        f = grid[:]
        
        # init
        f[0][0] = grid[0][0]
        for row in range(1, m):
            f[row][0] = f[row-1][0] + grid[row][0]
        for col in range(1, n):
            f[0][col] = f[0][col-1] + grid[0][col]
        
        # function
        for row in range(1, m):
            for col in range(1, n):
                f[row][col] = min(f[row-1][col], f[row][col-1]) + grid[row][col]
        
        return f[m-1][n-1]
```