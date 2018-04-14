### [98\. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/description/)

Difficulty: **Medium**



Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

*   The left subtree of a node contains only nodes with keys **less than** the node's key.
*   The right subtree of a node contains only nodes with keys **greater than** the node's key.
*   Both the left and right subtrees must also be binary search trees.

**Example 1:**  

```
    2
   / \
  1   3
```

Binary tree `[2,1,3]`, return true.

**Example 2:**  

```
    1
   / \
  2   3
```

Binary tree `[1,2,3]`, return false.


#### 解题思路
1. BST inorder traversal <=> increasing sequence
2. root 如果比左子树最大的值大，则比左子树大； 如果比右子树最小的值小，则比右子树小


#### Solution
```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
​
class Solution:
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if root is None:
            return True
        return self.valid(root, float("inf"), float("-inf"))
        
    def valid(self, root, max_val, min_val):
        if root is None:
            return True
        if root.val <= min_val or root.val >= max_val:
            return False
        return self.valid(root.left, root.val, min_val) and self.valid(root.right, max_val, root.val)
    
```
