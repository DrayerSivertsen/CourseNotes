# LeetCode Patterns

## Arrays

### Prefix Sums
Slices of array values that start at the beginning of the array. 
Sum meaning a sum of the values

Dynamic programming can be used on the prefix slice as it expands or shrinks

Prefix: every subarray starts at the beginning
Postfix: every subarray starts at the end

Problems can almost always be done interchangibly with postfix

Common use case: 
* eliminate repeated work
* precomputing work to make new operations easier

Notes: precompute the prefix sums in __init__

```
class PrefixSum:

    def __init__(self, nums):
        self.prefix = []
        total = 0
        for n in nums:
            total += n
            self.prefix.append(total)
        
    def rangeSum(self, left, right):
        preRight = self.prefix[right]
        preLeft = self.prefix[left - 1] if left > 0 else 0
        return (preRight - preLeft)
```