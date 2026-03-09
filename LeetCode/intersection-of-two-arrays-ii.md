# Intersection of Two Arrays II

Problem Link: https://leetcode.com/problems/intersection-of-two-arrays-ii/

## Python (your approach)

Approach:
- Traverse `nums1`.
- If element exists in `nums2`, add to result.
- Remove one occurrence from `nums2` so duplicates are handled correctly.

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        result=[]
        for i in nums1:
            if (i in nums2):
                result.append(i)
                nums2.remove(i)
        return result
```

## Python (anagram-style counting logic)

Approach:
- Same frequency idea as valid anagram.
- Count occurrences from `nums1`.
- While traversing `nums2`, pick values only if count is still available.

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        d = {}
        result = []

        for x in nums1:
            d[x] = d.get(x, 0) + 1

        for x in nums2:
            if x in d and d[x] > 0:
                result.append(x)
                d[x] -= 1

        return result
```

## C++ (your approach)

Approach:
- Use `unordered_map` to store counts from `nums1`.
- Traverse `nums2`, and whenever count exists, add to result and decrement count.

```cpp
class Solution { 
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<int,int> mp;
        vector<int> result;
        for(int x : nums1){
            mp[x]++;
        }
        for(int x : nums2){
            if(mp[x] > 0){
                result.push_back(x);
                mp[x]--;
            }
        }
        return result;
    }
};
```

## C++ (anagram-style counting logic)

Approach:
- Exactly same frequency-count idea used in anagram.
- Count first array, consume counts with second array.

```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<int, int> freq;
        vector<int> result;

        for (int x : nums1) {
            freq[x]++;
        }

        for (int x : nums2) {
            if (freq.find(x) != freq.end() && freq[x] > 0) {
                result.push_back(x);
                freq[x]--;
            }
        }

        return result;
    }
};
```

## Learning Note

In Python, I was getting partial passes at first.
Then I realized one matched value must be consumed each time, so adding `nums2.remove(i)` fixed duplicate-related cases.

In C++, I kept the same frequency-count concept from anagram, changed it a bit for arrays, and it worked cleanly.

Note: I used frequency counting as an experiment, it actually worked, and I immediately followed the sacred rule: if it works, don’t touch it.
