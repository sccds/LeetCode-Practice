### [144\. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)

Difficulty: **Medium**



Given a binary tree, return the _preorder_ traversal of its nodes' values.

For example:  
Given binary tree `[1,null,2,3]`,  

```
   1
    \
     2
    /
   3
```

return `[1,2,3]`.

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
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        result = list()
        self.traversal(root, result)
        return result
        
    def traversal(self, root, result):
        if root is None:
            return []
        result.append(root.val)
        self.traversal(root.left, result)
        self.traversal(root.right, result)
        
```