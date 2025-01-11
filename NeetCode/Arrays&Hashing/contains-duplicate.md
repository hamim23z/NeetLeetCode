# Neetcode 150 - Arrays and Hashing - Contains Duplicate (217)


```
**Problem Breakdown**
-> Given an array of integers called nums, return True if any value appears at least twice in the array and return False if
every element is distinct.

nums = [1,2,3,4] #False
nums = [1,1,1,1] #True
```

<br>
<br>

```
**Solution**
-> There are a couple of different solutions to this. The first being brute force. We look at the first number and then we
compare it to the rest. We do the same for first, second, third, etc number. This takes O(n^2) time and space is O(1).

-> The second solution is done by sorting. We take an array and then we sort it in ascending order. This is helpful because
if there are any distinct values, they are next to each other. And instead of having to compare each number to each other,
which takes a lot of time, the numbers will be right next to each other. So we only **iterate through the array once**, thus
saving us time. This takes O(nlogn). Space is O(1).

-> The third solution and the one I did, is the hashset. So we start off with an empty set and then using the first number in
our array we begin. Since it is an empty set, there are no numbers in the hashset but we put the first number. Then we check
the second number and if it is in the hashset, it's a duplicate, or else it is not. We continue this process. Time and space
are both O(n).
    -> Say we have [1,2,3,1]. 1 goes in the hashset, then we go to 2. 2 is not in the hashset so we put it in there. Then we
       go to 3. 3 is not in the hashset so it goes in there. Then we go to 1. 1 is already in the hashset, so we know that it
       is a duplicate so it returns True. 
```

<br>
<br>

```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        hashset = set()

        for num in nums:
            if num in hashset:
                return True
            else:
                hashset.add(num)
        return False
