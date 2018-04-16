### [62\. Unique Paths](https://leetcode.com/problems/unique-paths/description/)

Difficulty: **Medium**

A robot is located at the top-left corner of a _m_ x _n_ grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![](https://leetcode.com/static/images/problemset/robot_maze.png)

Above is a 3 x 7 grid. How many possible unique paths are there?

**Note:** _m_ and _n_ will be at most 100.


#### Solution
```python
class Solution:
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        if m == 0 or n == 0:
            return 0
        
        # define and init
        f = [[1 for _ in range(n)] for _ in range(m)]
        
        # function
        for row in range(1, m):
            for col in range(1, n):
                f[row][col] = f[row-1][col] + f[row][col-1]
                
        return f[m-1][n-1]
        
```