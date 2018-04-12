### [145\. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)

Difficulty: **Hard**



Given a binary tree, return the _postorder_ traversal of its nodes' values.

For example:  
Given binary tree `[1,null,2,3]`,

```
   1
    \
     2
    /
   3
```

return `[3,2,1]`.

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
    def postorderTraversal(self, root):
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
        self.traverse(root.right, result)
        result.append(root.val)
```