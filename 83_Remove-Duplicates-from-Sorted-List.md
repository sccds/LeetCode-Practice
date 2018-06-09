### [83\. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/)

Difficulty: **Easy**

Given a sorted linked list, delete all duplicates such that each element appear only _once_.

**Example 1:**

```
**Input:** 1->1->2
**Output:** 1->2
```

**Example 2:**

```
**Input:** 1->1->2->3->3
**Output:** 1->2->3
```



#### Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
​
class Solution:
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head is None:
            return None
        
        node = head
        while node.next is not None:
            if node.val == node.next.val:
                node.next = node.next.next
            else:
                node = node.next
        return head
```