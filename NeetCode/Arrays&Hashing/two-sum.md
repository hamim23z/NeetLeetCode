# Neetcode 150 - Arrays and Hashing - Two Sum (1)

```
**Problem Breakdown**
-> Let's say we have an array of integers called numbers and we have another variable called target. We want to
return the indices of the two numbers so that they add up to the value of target. Target is also an integer. We
also assume that each input will have one solution and we can't use the same element twice, this means that we
can't use the same index twice but if they are the same number in different index, then we can use it. 
nums = [2,7,9,11] and target = 9 #[0,1] because 2 and 7 add up to 9. 
```

<br>
<br>

```
**Solution(s)**
-> The first solution can be brute force. Let's say we have an array of the four numbers and we have a target. In
order to find the numbers that add up to the target, we need to check every element and each index and try different
combinations. [2,11,15,7] and our target is 9. Start at index 0 aka 2. And then check 2+11, 2+15, and 2+7. Lucky for
us, 2+7=9. We go through the array entirely. Thus the time complexity is O(n^2).


-> The other solution is a hashmap, doing it in one pass. So we make a hashmap and then we store the value and the
index of the value. The way this will work is given our target, we will go through the values and then subtract it.
Upon doing so, we store the value and index inside the hashmap. And the reason this works is because, we do make
one pass throughout the entire array and because we know that a solution exists, it will also exist in our hashmap.
Say we have the new array of [2,1,5,3]. 4-2=2 and then we put value 2 and index 0 into our hashmap. Then we move
onto 1, 4-1=3 and then we put value 1 and index 1 into our hashmap. Then 4-5=-1, so we put value 5 and index 2 into
our hashmap. Lastly, 4-3=1. We already have 1 in our hashmap. So we know that we need to return [1,3]. We know that
once we visit the first element that sums to our target, our hashmap will only go that far. But once we reach the
second element, we know it is not in the hashmap yet. So once we visit the second element, the first element is
already in it. The time complexity is O(n). And space is also O(n).
```

<br>

### Solution 1 (Hashmap)
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashmap = {}

        for i, n in enumerate(nums):
            diff = target - n
            if diff in hashmap:
                return [hashmap[diff], i]
            else:
                hashmap[n] = i
        return
```
