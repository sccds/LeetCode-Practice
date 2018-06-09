### [82\. Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/)

Difficulty: **Medium**


Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only _distinct_ numbers from the original list.

**Example 1:**

```
**Input:** 1->2->3->3->4->4->5
**Output:** 1->2->5
```

**Example 2:**

```
**Input:** 1->1->1->2->3
**Output:** 2->3
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
        dummy = ListNode(0)
        dummy.next = head
        head = dummy
        
        while head.next is not None and head.next.next is not None:
            if head.next.val == head.next.next.val:
                val = head.next.val
                while head.next is not None and head.next.val == val:
                    head.next = head.next.next
            else:
                head = head.next
                
        return dummy.next
```