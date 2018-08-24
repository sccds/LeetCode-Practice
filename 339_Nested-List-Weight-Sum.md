### [339\. Nested List Weight Sum](https://leetcode.com/problems/nested-list-weight-sum/description/)

Difficulty: **Easy**

Given a nested list of integers, return the sum of all integers in the list weighted by their depth.

Each element is either an integer, or a list -- whose elements may also be integers or other lists.


**Example 1:**

```
**Input:** <span id="example-input-1-1" style="display: inline;">[[1,1],2,[1,1]]</span>
**Output:** <span id="example-output-1" style="display: inline;">10</span> 
**Explanation:** Four 1's at depth 2, one 2 at depth 1.```
```

**Example 2:**

```
**Input:** <span id="example-input-2-1" style="display: inline;">[1,[4,[6]]]</span>
**Output:** <span id="example-output-2" style="display: inline;">27</span> 
**Explanation:** One 1 at depth 1, one 4 at depth 2, and one 6 at depth 3; 1 + 4*2 + 6*3 = 27.```
```


#### Solution

Language: **Python3**

```python
# """
# This is the interface that allows for creating nested lists.
# You should not implement it, or speculate about its implementation
# """
#class NestedInteger:
#    def __init__(self, value=None):
#        """
#        If value is not specified, initializes an empty list.
#        Otherwise initializes a single integer equal to value.
#        """
#
#    def isInteger(self):
#        """
#        @return True if this NestedInteger holds a single integer, rather than a nested list.
#        :rtype bool
#        """
#
#    def add(self, elem):
#        """
#        Set this NestedInteger to hold a nested list and adds a nested integer elem to it.
#        :rtype void
#        """
#
#    def setInteger(self, value):
#        """
#        Set this NestedInteger to hold a single integer equal to value.
#        :rtype void
#        """
#
#    def getInteger(self):
#        """
#        @return the single integer that this NestedInteger holds, if it holds a single integer
#        Return None if this NestedInteger holds a nested list
#        :rtype int
#        """
#
#    def getList(self):
#        """
#        @return the nested list that this NestedInteger holds, if it holds a nested list
#        Return None if this NestedInteger holds a single integer
#        :rtype List[NestedInteger]
#        """
​
class Solution:
    def depthSum(self, nestedList):
        """
        :type nestedList: List[NestedInteger]
        :rtype: int
        """
        return self.get_sum(nestedList, 1)
    
    def get_sum(self, nestedList, level):
        res = 0
        for item in nestedList:
            if item.isInteger():
                res += item.getInteger() * level
            else:
                res += self.get_sum(item.getList(), level + 1)
        return res
            
        
```