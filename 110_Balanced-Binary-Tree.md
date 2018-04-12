### [110\. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/description/)

Difficulty: **Easy**



Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

> a binary tree in which the depth of the two subtrees of _every_ node never differ by more than 1.

**Example 1:**

Given the following tree `[3,9,20,null,null,15,7]`:

```
    3
   / \
  9  20
    /  \
   15   7```

Return true.  

**Example 2:**

Given the following tree `[1,2,2,3,3,null,null,4,4]`:

```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```

Return false.

#### 思路
左子树balanced, 右子树balanced, 左右子树深度相差不超过1


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
    def isBalanced(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if root is None:
            return True
        return self.isBalanced(root.left) and self.isBalanced(root.right) and abs(self.max_path(root.left) - self.max_path(root.right)) <= 1
        
​
    def max_path(self, root):
        if root is None:
            return 0
        return max(self.max_path(root.left), self.max_path(root.right)) + 1
```