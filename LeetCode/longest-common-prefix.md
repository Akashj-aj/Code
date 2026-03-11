# Longest Common Prefix

Problem Link: https://leetcode.com/problems/longest-common-prefix/

## Python

Approach:
- Start with the first string as the current prefix.
- Compare it with every other string.
- While the current prefix does not match the starting part of the current string, reduce the prefix by one character.
- If the prefix becomes empty, return `""`.

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        pref = strs[0]
        pref_len = len(pref)

        for s in strs[1:]:
            while pref != s[0:pref_len]:
                pref_len -= 1
                if pref_len == 0:
                    return ""
                
                pref = pref[0:pref_len]
        
        return pref
```

## C++

Approach:
- Take the first string as the current prefix.
- Compare it with each next string.
- If it does not match the starting part of that string, keep reducing the prefix.
- If prefix length becomes `0`, return empty string.

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return "";

        string pref = strs[0];
        int prefLen = pref.length();

        for (int i = 1; i < strs.size(); i++) {
            string s = strs[i];
            while (prefLen > s.length() || pref != s.substr(0, prefLen)) {
                prefLen--;
                if (prefLen == 0) {
                    return "";
                }
                pref = pref.substr(0, prefLen);
            }
        }

        return pref;        
    }
};
```

## Learning Note

I tried to solve this one, but I could not figure out the logic on my own.
I was also not in the mood to keep thinking about it, so I checked the solution tab and wrote the code from there.
Still, after reading the explanation, I understood how the prefix keeps shrinking until it matches all strings.

Note: I went to the solution tab for a hint and returned with the full download.
