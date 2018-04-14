### [103\. Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/)

Difficulty: **Medium**



Given a binary tree, return the _zigzag level order_ traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).

For example:  
Given binary tree `[3,9,20,null,null,15,7]`,  

```
    3
   / \
  9  20
    /  \
   15   7
```

return its zigzag level order traversal as:  

```
[
  [3],
  [20,9],
  [15,7]
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
    def zigzagLevelOrder(self, root):
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
        num = 0
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
            if num % 2 == 0:
                result.append(level)
            else:
                result.append(level[::-1])
            num += 1
        return result
            
```