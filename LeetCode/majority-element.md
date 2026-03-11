# Majority Element

Problem Link: https://leetcode.com/problems/majority-element/

## Python

Approach:
- Use a dictionary to count the frequency of each number.
- Traverse the dictionary items.
- If any value is greater than `len(nums) / 2`, return its key.

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        d={}
        for i in nums:
            d[i]=d.get(i,0)+1
        for key,val in d.items():
            if val > (len(nums)/2):
                return key
```

## C++

Approach:
- Use `unordered_map` to count the frequency of each number.
- Traverse the map.
- If the count is greater than `nums.size() / 2`, return that number.

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        
        unordered_map<int,int> mp;

        for(int x : nums){
            mp[x]++;
        }

        for(auto i : mp){
            if(i.second > nums.size() / 2){
                return i.first;
            }
        }

        return -1;
    }
};
```

## Learning Note

In this problem, I got to know how to access keys and values from a dictionary in Python using `.items()`.
In C++, accessing key and value from `unordered_map` felt easier to follow.

Note: Same frequency idea again, just with key-value access getting all the attention this time.
