### [226\. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/)

Difficulty: **Easy**



Invert a binary tree.

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9```

to

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1```

**Trivia:**  
This problem was inspired by by :

> Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so f*** off.



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
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root is None:
            return None
        root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
        return root
```