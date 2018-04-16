### [70\. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

Difficulty: **Easy**

You are climbing a stair case. It takes _n_ steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given _n_ will be a positive integer.

**Example 1:**

```
**Input:** 2
**Output:**  2
**Explanation:**  There are two ways to climb to the top.

1\. 1 step + 1 step
2\. 2 steps
```

**Example 2:**

```
**Input:** 3
**Output:**  3
**Explanation:**  There are three ways to climb to the top.

1\. 1 step + 1 step + 1 step
2\. 1 step + 2 steps
3\. 2 steps + 1 step
```



#### Solution
```python
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <= 2:
            return n
        
        # init
        f = list(range(n+1))
        f[0] = 1
        f[1] = 1
        for i in range(2, n+1):
            f[i] = f[i-1] + f[i-2]
            
        return f[-1]
```