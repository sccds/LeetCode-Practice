### [124\. Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)

Difficulty: **Hard**



Given a binary tree, find the maximum path sum.

For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain **at least one node** and does not need to go through the root.

For example:  
Given the below binary tree,

```
       1
      / \
     2   3
```

Return `6`.


#### 解题思路
**复杂版**
1. 这条路径**必须**包含至少一个点
2. 节点的value可以 < 0
3. 任意点到任意点

包含几种情况：
1. 左子树的max, 
2. 右子树的max,
3. 还有一种情况，是跨根节点路径 => root.val + 左子树 single path + 右子树 single path

**简化版** => simply path / single path
1. 这条路径可以不包含点 => return 0
2. 节点的value可以 < 0
3. 从 root 到任意点


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
    def maxPathSum(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        return self.helper(root)[1]
        
    def helper(self, root): # return single_path, max_path
        if root is None:
            return 0, float("-inf")
        
        # divide
        left = self.helper(root.left)
        right = self.helper(root.right)
        
        # conquer
        single_path = max(0, max(left[0], right[0]) + root.val)
        max_path = max(left[1], right[1], left[0] + right[0] + root.val)
        return single_path, max_path
        
    def root_to_any(self, root):
        if root is None:
            return 0
        left = self.root_to_any(root.left)
        right = self.root_to_any(root.right)
        return max(0, max(left, right) + root.val)
​
```
