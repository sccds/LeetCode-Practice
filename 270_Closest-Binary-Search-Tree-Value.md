### [270\. Closest Binary Search Tree Value](https://leetcode.com/problems/closest-binary-search-tree-value/description/)

Difficulty: **Easy**


Given a non-empty binary search tree and a target value, find the value in the BST that is closest to the target.

**Note:**

*   Given target value is a floating point.
*   You are guaranteed to have only one unique value in the BST that is closest to the target.

**Example:**

```
**Input:** root = [4,2,5,1,3], target = 3.714286

    4
   / \
  2   5
 / \
1   3

**Output:** 4
```


#### Solution

Language: **Python3**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
​
class Solution:
    def closestValue(self, root, target):
        """
        :type root: TreeNode
        :type target: float
        :rtype: int
        """
        self.diff = float('inf')
        self.res = root.val
        self.find_min(root, target)
        return self.res
        
        
    def find_min(self, root, target):
        if root is None:
            return
        df = abs(root.val - target)
        if df < self.diff:
            self.diff = df
            self.res = root.val
        self.find_min(root.left, target)
        self.find_min(root.right, target)
```