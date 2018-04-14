### [107\. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/)

Difficulty: **Easy**



Given a binary tree, return the _bottom-up level order_ traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,  

```
    3
   / \
  9  20
    /  \
   15   7
```

return its bottom-up level order traversal as:  

```
[
  [15,7],
  [9,20],
  [3]
]
```



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
    def levelOrderBottom(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        result = list()
        if root is None:
            return result
        from queue import Queue
        q = Queue()
        q.put(root)
        while not q.empty():
            level = list()
            size = q.qsize()
            for _ in range(size):
                tail = q.get()
                if tail.left:
                    q.put(tail.left) 
                if tail.right:
                    q.put(tail.right)
                level.append(tail.val)
            result.append(level)
        return result[::-1]
            
```