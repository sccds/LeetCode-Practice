### [111\. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)

Difficulty: **Easy**



Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.



#### Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
​
class Solution:
    def minDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if root is None:
            return 0
        return self.get_min(root)
    
    def get_min(self, root):
        if root is None:
            return float("inf")
        if root.left is None and root.right is None:
            return 1
        return min(self.get_min(root.left), self.get_min(root.right)) + 1
```