# Valid Anagram

Problem Link: https://leetcode.com/problems/valid-anagram/

## Python

Approach:
- If lengths are different, return `False`.
- Count frequency of characters in `s`.
- Decrease counts while traversing `t`.
- If any character is missing or count goes below needed, return `False`.
- If all checks pass, return `True`.

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        d={}
        for char in s:
            d[char]=d.get(char,0)+1
        for char in t:
            if char not in d or d[char]==0:
                return False
            d[char]-=1
        return True
```

## C++

Approach:
- Build frequency maps for both strings.
- Compare both maps.
- If equal, strings are anagrams.

```cpp
#include <map>
class Solution {
public:
    bool isAnagram(string s, string t) {
        map<char,int> um;
        for (char ch:s){
            um[ch]++;
        }
        map<char,int> um2;
        for (char ch:t){
            um2[ch]++;
        }
        return um==um2;
    }
};
```

## C++ (`unordered_map`)

Approach:
- Check length first.
- Count chars from `s`.
- Reduce counts while traversing `t`.
- If any count is already zero, return `false`.

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        
        if(s.length() != t.length())
            return false;

        unordered_map<char,int> mp;

        for(char c : s){
            mp[c]++;
        }

        for(char c : t){
            if(mp[c] == 0)
                return false;
            mp[c]--;
        }

        return true;
    }
};
```

## Learning Note

I did not struggle in this problem.
The frequency-count idea was clear and easy to apply.

Note: Rare moment when the first approach worked without any debugging drama.
