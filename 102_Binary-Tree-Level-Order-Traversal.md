### [102\. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)

Difficulty: **Medium**



Given a binary tree, return the _level order_ traversal of its nodes' values. (ie, from left to right, level by level).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,  

```
    3
   / \
  9  20
    /  \
   15   7
```

return its level order traversal as:  

```
[
  [3],
  [9,20],
  [15,7]
]
```

#### 解题思路
1. 2 Queues
2. Queue + Dummy Node
3. 1 Queue (best)


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
    def levelOrder(self, root):
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
        return result
        
```
