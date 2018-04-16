### [63\. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/description/)

Difficulty: **Medium**


Follow up for "Unique Paths":

Now consider if some obstacles are added to the grids. How many unique paths would there be?

An obstacle and empty space is marked as `1` and `0` respectively in the grid.

For example,

There is one obstacle in the middle of a 3x3 grid as illustrated below.

```
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
```

The total number of unique paths is `2`.

**Note:** _m_ and _n_ will be at most 100.



#### Solution
```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        m = len(obstacleGrid)
        n = len(obstacleGrid[0])
        if m == 0 or n == 0:
            return 0
        
        # define and init
        f = [[0 for _ in range(n)] for _ in range(m)]
             
        for i in range(m):
            if obstacleGrid[i][0] != 1:
                f[i][0] = 1
            else:
                break
        
        for j in range(n):
            if obstacleGrid[0][j] != 1:
                f[0][j] = 1
            else:
                break 
​
        # function
        for row in range(1, m):
            for col in range(1, n):
                if obstacleGrid[row][col] != 1:
                    f[row][col] = f[row-1][col] + f[row][col-1]
                else:
                    f[row][col] = 0
        
        return f[m-1][n-1]
```