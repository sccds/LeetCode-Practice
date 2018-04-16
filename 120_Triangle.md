### [120\. Triangle](https://leetcode.com/problems/triangle/description/)

Difficulty: **Medium**



Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

For example, given the following triangle

```
[
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

The minimum path sum from top to bottom is `11` (i.e., 2 + 3 + 5 + 1 = 11).

**Note:**  
Bonus point if you are able to do this using only _O_(_n_) extra space, where _n_ is the total number of rows in the triangle.


#### 解题思路

x, y => x + 1, y  左下  
     => x + 1, y + 1 右下


#### Solution

**Traverse: O(2^N) => Time Limit Exceed**
```python
class Solution:
    def minimumTotal(self, triangle):
        """
        :type triangle: List[List[int]]
        :rtype: int
        """
        self.triangle = triangle
        self.best = float("inf")
        self.traverse(0, 0, 0)
        return self.best
        
    def traverse(self, x, y, summ):
        if x == len(self.triangle):
            if summ < self.best:
                self.best = summ
            return
        self.traverse(x + 1, y, summ + self.triangle[x][y])
        self.traverse(x + 1, y + 1, summ + self.triangle[x][y])
            

```


**Divide and Conquer: O(2^N) => Time Limit Exceed**
```python
class Solution:
    def minimumTotal(self, triangle):
        """
        :type triangle: List[List[int]]
        :rtype: int
        """
        self.triangle = triangle
        return self.divide_conquer(0, 0)
        

    def divide_conquer(self, x, y):
        if x == len(self.triangle):
            return 0
        return self.triangle[x][y] + min(self.divide_conquer(x + 1, y), self.divide_conquer(x + 1, y + 1))
```

**Divide and Conquer with memorize: O(N^2)**
```python
class Solution:
    def minimumTotal(self, triangle):
        """
        :type triangle: List[List[int]]
        :rtype: int
        """
        self.triangle = triangle
        self.trangle_mem = dict()
        return self.divide_conquer(0, 0)
        

    def divide_conquer(self, x, y):
        if x == len(self.triangle):
            return 0
        if self.trangle_mem.get((x, y)):
            return self.trangle_mem[(x, y)]
        self.trangle_mem[(x, y)] = self.triangle[x][y] + min(self.divide_conquer(x + 1, y), self.divide_conquer(x + 1, y + 1))
        return self.trangle_mem[(x, y)]
```

**自底向上**
动归状态矩阵 f[i][j] => 表示从 i,j 出发走到最后一层的最小路径长度

```python
class Solution:
    def minimumTotal(self, triangle):
        """
        :type triangle: List[List[int]]
        :rtype: int
        """
        f = triangle[:]
        n = len(triangle)
            
        # 初始化，终点先有值
        for i in range(n):
            f[n-1][i] = triangle[n-1][i]
        
        # 循环求解
        for i in range(n-2, -1, -1):
            for j in range(i+1):
                f[i][j] = min(f[i+1][j], f[i+1][j+1]) + triangle[i][j]
                
        return f[0][0]
```

**自顶向下**
动归状态矩阵 f[i][j] => 表示从 0,0 出发, 走到 i, j 的最小路径长度

```python
class Solution:
    def minimumTotal(self, triangle):
        """
        :type triangle: List[List[int]]
        :rtype: int
        """
        f = triangle.copy()
        n = len(triangle)
            
        # 初始化
        f[0][0] = triangle[0][0]
        
        # 循环求解
        for i in range(1, n):
            for j in range(len(triangle[i])):
                if j-1 >= 0 and j < len(triangle[i-1]):   # 左上角存在，右上角也存在
                    f[i][j] = min(f[i-1][j-1], f[i-1][j]) + triangle[i][j]
                elif j-1 >= 0:                            # 只有左上角存在
                    f[i][j] = f[i-1][j-1] + triangle[i][j]
                else:                                     # 只有右上角存在
                    f[i][j] = f[i-1][j] + triangle[i][j]
                
        return min(f[n-1])
```

