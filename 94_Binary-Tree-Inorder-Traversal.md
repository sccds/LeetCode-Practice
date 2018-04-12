### [94\. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/description/)

Difficulty: **Medium**



Given a binary tree, return the _inorder_ traversal of its nodes' values.

For example:  
Given binary tree `[1,null,2,3]`,  

```
   1
    \
     2
    /
   3
```

return `[1,3,2]`.

**Note:** Recursive solution is trivial, could you do it iteratively?



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
    def inorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        result = list()
        self.traverse(root, result)
        return result
    def traverse(self, root, result):
        if root is None:
            return []
        self.traverse(root.left, result)
        result.append(root.val)
        self.traverse(root.right, result)
```