### [589\. N-ary Tree Preorder Traversal](https://leetcode.com/problems/n-ary-tree-preorder-traversal/description/)

Difficulty: **Easy**



Given an n-ary tree, return the _preorder_ traversal of its nodes' values.

For example, given a `3-ary` tree:

![](/static/images/problemset/NaryTreeExample.png)

Return its preorder traversal as: `[1,3,5,6,2,4]`.

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
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        res = list()
        if not root:
            return res
        res.append(root.val)
        for node in root.children:
            res.extend(self.preorder(node))
        return res
```