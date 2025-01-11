# Neetcode 150 - Arrays and Hashing - Valid Anagrams (242)

```
**Problem Breakdown**
-> Let's say we have two strings s and t. We will return True if t is an anagram of s. Otherwise, we will return False.
s = 'racecar' and t = 'carrace' #True
s = 'rat' and t = 'car' #False
```

<br>
<br>

```
**Solution(s)**
-> One solution to this is using a hashmap. The way it works is that we will have two different hashmaps, one for s and one
for t. The key is the character and the value is the count. We go through the keys for each hashmap and compare the count.
We iterate through this. A plus side is that if we know the length of both s and t, we only have to iterate through one of
them. Time is O(s+t). Space is O(s+t). This uses a manual hashmap. 

-> Another solution is to sort them. We can force an ordering of these by sorting it in alphabetical order. We then check if
the sorted versions are the same or not. Time is O(nlogn). Space is O(n). This is probably the simplest solution coding wise.

-> The third solution is to use the frequency and dictionaries, similar to a hashmap. But this time, we are utilizing Python
to our advantage. It goes through the two different dictionaries and checks if all the keys in one are in the other. It also
checks if the values are the same for each key. 
```

<br>

### Solution 1 (The One I Submitted - Using Frequencies)
```python
from collections import Counter
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        
        s_dict = Counter(s)
        t_dict = Counter(t)

        return s_dict == t_dict
```

<br>

### Solution 2 (Sorting)
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```

<br>

### Solution 3 (Hashmaps - Pulled This From Neetcode Solution)
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS, countT = {}, {}

        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)
        return countS == countT
```
