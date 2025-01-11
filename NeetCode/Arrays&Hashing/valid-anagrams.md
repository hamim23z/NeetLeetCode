# Neetcode 150 - Arrays and Hashing - Valid Anagrams (242)

```
**Problem Breakdown**
-> Let's say we have two strings s and t. We will return True if t is an anagram of s. Otherwise, we will return
False. 
s = 'racecar' and t = 'carrace' #True
s = 'rat' and t = 'car' #False
```

<br>
<br>

```
**Solution(s)**
-> One solution to this is using a Hashmap. The way it works is that we'll have two different hashmaps, one for s
and another for t. The key is the character and the value is the count. We go through the kets for each hashmap and
compare the count. We iterate through this. A plus side is that if we know the length of both s and t, we only have
to iterate through one of them. Time is O(s+t). And space is O(s+t). This uses a manual hashmap.


-> The second solution is to sort them. When talking about sorting, it means to sort them in alphabetical order. And
once we do this, all we have to do is check if the sorted version of them are equal to each other, thus returning
either True or False.


-> The third solution, and the one I used, is to use a frequency counter. It is similar to a manual hashmap but this
time we are using Python to our advantage. The way it works is that for s and t, it creates a frequency dictionary for
each. And then it goes through all the keys in f and checks if that key is in g as well. It also checks if the values
are the same for each key. The time complexity is O(n). 
```

<br>

### Solution 1 (Frequency Dictionary Method)
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

### Solution 2 (Sorting Method)
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```

<br>

### Solution 3 (Hashmap Method - Pulled From Neetcode Solution)
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
