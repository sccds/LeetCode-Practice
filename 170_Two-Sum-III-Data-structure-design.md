### [170\. Two Sum III - Data structure design](https://leetcode.com/problems/two-sum-iii-data-structure-design/description/)

Difficulty: **Easy**



Design and implement a TwoSum class. It should support the following operations: `add` and `find`.

`add` - Add the number to an internal data structure.  
`find` - Find if there exists any pair of numbers which sum is equal to the value.

For example,  

```
add(1); add(3); add(5);
find(4) -> true
find(7) -> false
```



#### Solution
```python
class TwoSum:
​
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.num_dict = dict()
        
​
    def add(self, number):
        """
        Add the number to an internal data structure..
        :type number: int
        :rtype: void
        """
        self.num_dict[number] = 1 if number not in self.num_dict else 2
        
​
    def find(self, value):
        """
        Find if there exists any pair of numbers which sum is equal to the value.
        :type value: int
        :rtype: bool
        """
        for key in self.num_dict:
            other = value - key
            if other in self.num_dict and (2 * key != value or self.num_dict[other] == 2):
                return True
        return False
            
​
​
# Your TwoSum object will be instantiated and called as such:
# obj = TwoSum()
# obj.add(number)
# param_2 = obj.find(value)
```