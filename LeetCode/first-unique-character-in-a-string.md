# First Unique Character in a String

Problem Link: https://leetcode.com/problems/first-unique-character-in-a-string/

## Python (index loop)

Approach:
- Count frequency of each character.
- Traverse string by index.
- Return first index where frequency is `1`.

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        d={}
        for c in s:
            d[c]=d.get(c,0)+1
        for i in range(len(s)):
            if d[s[i]] == 1:
                return i
        return -1
```

## Python (`enumerate`)

Approach:
- Same frequency logic.
- Use `enumerate` to get both index and character directly.

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        d={}
        for c in s:
            d[c]=d.get(c,0)+1
        for i,c in enumerate(s):
            if d[c]==1:
                return i
        return -1
```

## C++

Approach:
- Count character frequencies in `unordered_map`.
- Traverse string again and return first index with count `1`.

```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char, int> freq;

        for (char c : s) {
            freq[c]++;
        }

        for (int i = 0; i < s.size(); i++) {
            if (freq[s[i]] == 1) {
                return i;
            }
        }

        return -1;        
    }
};
```

## Learning Note

I saw others using enumerate() and realized I was writing extra lines just to suffer.
For C++, I copied the same frequency idea from Python and only changed syntax.

Note: New language, same logic, same frequency map doing all the hard work while I take credit.
