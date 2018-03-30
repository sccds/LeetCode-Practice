### [653\. Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)

Difficulty: **Easy**



Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

**Example 1:**  

```
**Input:** 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

**Output:** True
```

**Example 2:**  

```
**Input:** 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

**Output:** False
```



#### Solution
```
class Solution:
    def findTarget(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: bool
        """
        num_set = set([])
        return self.find(root, k, num_set)
    def find(self, root, k, num_set):
        if root is None:
            return False
        if k - root.val in num_set:
            return True
        num_set.add(root.val)
        return self.find(root.left, k, num_set) or self.find(root.right, k, num_set)
​
```