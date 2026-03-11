# 219. Contains Duplicate II

Problem Link: https://leetcode.com/problems/contains-duplicate-ii/

## Python

Approach:
- Use a dictionary to store the last index of each number.
- Traverse the array.
- If the current number was seen before, check the difference between current index and previous index.
- If that difference is less than or equal to `k`, return `True`.
- Otherwise, update the index of the current number.

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        d={}
        for i in range(len(nums)):
            if nums[i] in d and i - d[nums[i]] <=k:
                return True
            else:
                d[nums[i]]=i
        return False
```

## Python (`enumerate`)

Approach:
- Same logic, but use `enumerate()` to get index and value together.
- This makes dictionary access a little cleaner.

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        seen = {}

        for i, val in enumerate(nums):
            if val in seen and i - seen[val] <= k:
                return True
            else:
                seen[val] = i
        
        return False
```

## C++

Approach:
- Use `unordered_map` to store the last index of each number.
- Traverse the array.
- If the number already exists in the map, check the index difference.
- If the difference is within `k`, return `true`.
- Otherwise, update its latest index.

```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int, int> d;

        for (int i = 0; i < nums.size(); i++) {
            int num = nums[i];
            if (d.find(num) != d.end() && i - d[num] <= k) {
                return true;
            }
            d[num] = i;
        }
        return false;        
    }
};
```

## Learning Note

I understood the main idea first, but I had to think a little about how to use the dictionary to store the last index and access it properly.
Once that part clicked, the logic became simple.

Note: The logic was not that hard, but my brain still paused like `d[num]` was some advanced technology.
