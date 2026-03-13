# Group Anagrams

Problem Link: https://leetcode.com/problems/group-anagrams/

## Python

Approach:
- Use a dictionary where the key is the sorted version of a word.
- Words with the same sorted characters are anagrams, so they go into the same group.
- At the end, return all dictionary values.

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        d = {}
        for word in strs:
            key = "".join(sorted(word))
            if key not in d:
                d[key] = []
            d[key].append(word)

        return list(d.values())
```

## C++

Approach:
- Use `unordered_map<string, vector<string>>`.
- Sort each string to create a common key.
- Store the original word in the group for that key.
- Return all grouped values from the map.

```cpp
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string, vector<string>> mp;
        for(string s : strs){
            string key = s;
            sort(key.begin(), key.end()); 
            mp[key].push_back(s);
        }
        vector<vector<string>> result;
        for(auto x : mp){
            result.push_back(x.second);
        }

        return result;
    }
};
```

## Learning Note

I was not really in the mood to solve many questions that day, so my patience was already limited.
I tried this one, but I could not get the logic on my own.
After seeing others' solutions, I understood the idea of using the sorted word as the key and then wrote the code from that understanding.

Note: I went looking for the logic, found it in someone else's solution, and brought it back like it was group project work.
