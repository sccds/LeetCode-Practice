### [590\. N-ary Tree Postorder Traversal](https://leetcode.com/problems/n-ary-tree-postorder-traversal/description/)

Difficulty: **Easy**

Given an n-ary tree, return the _postorder_ traversal of its nodes' values.

For example, given a `3-ary` tree:

![](/static/images/problemset/NaryTreeExample.png)

Return its postorder traversal as: `[5,6,3,2,4,1]`.

**Note:** Recursive solution is trivial, could you do it iteratively?


#### Solution

Language: **Python**

```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res = []
        if not root:
            return res
        for node in root.children:
            res.extend(self.postorder(node))
        res.append(root.val)
        return res
```