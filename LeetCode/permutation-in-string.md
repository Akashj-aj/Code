# Permutation in String

Problem Link: https://leetcode.com/problems/permutation-in-string/

## Python

Approach:
- If `s1` is longer than `s2`, answer is immediately `False`.
- Use two dictionaries:
- `d1` stores frequency of characters in `s1`
- `d2` stores frequency of characters in the current window of `s2`
- First build both dictionaries for the first window of size `len(s1)`.
- If both dictionaries match, return `True`.
- Then slide the window:
- Add the new character on the right
- Remove the old character on the left
- If any count becomes `0`, delete that key
- Compare both dictionaries again

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False

        d1 = {}
        d2 = {}

        for i in range(len(s1)):
            d1[s1[i]] = 1 + d1.get(s1[i], 0)
            d2[s2[i]] = 1 + d2.get(s2[i], 0)

        if d1 == d2:
            return True

        left = 0
        for right in range(len(s1), len(s2)):
            d2[s2[right]] = 1 + d2.get(s2[right], 0)
            d2[s2[left]] -= 1

            if d2[s2[left]] == 0:
                del d2[s2[left]]

            left += 1

            if d1 == d2:
                return True

        return False
```

## C++

Approach:
- If `s1` is bigger than `s2`, return `false`.
- Use two `unordered_map`s:
- one for `s1`
- one for the current window in `s2`
- Build the first window.
- Then move the window one step at a time:
- add the new right character
- reduce the old left character
- erase it if count becomes `0`
- compare both maps

```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        if (s1.length() > s2.length()) {
            return false;
        }
        
        unordered_map<char, int> d1;
        unordered_map<char, int> d2;
        
        for (int i = 0; i < s1.length(); i++) {
            d1[s1[i]]++;
            d2[s2[i]]++;
        }
        
        if (d1 == d2) {
            return true;
        }
        
        int left = 0;
        for (int right = s1.length(); right < s2.length(); right++) {
            d2[s2[right]]++;
            d2[s2[left]]--;
            
            if (d2[s2[left]] == 0) {
                d2.erase(s2[left]);
            }
            
            left++;
            
            if (d1 == d2) {
                return true;
            }
        }
        
        return false;        
    }
};
```

## Learning Note

I came back to LeetCode after around two weeks, so the motivation was already on low battery.
I still got the basic idea that we need two dictionaries or hash maps and compare them.
That was apparently not enough, so I checked others' solutions and then understood the sliding-window part I was missing.

Note: I brought the basic idea, and someone else's solution kindly supplied the missing brain cells.
