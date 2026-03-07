# Contains Duplicate

## Python (Hash Map)

Approach: Track seen numbers in a dictionary. If a number repeats, return `True`.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        d={}
        for i in nums:
            if i in d:
                return True
            else:
                d[i]=1
        return False
```

## Python (Set Size Check)

Approach: Convert to set and compare lengths.

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums)!=len(set(nums))
```

## C++

Approach: Insert all elements into `set` and compare sizes.

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> s(nums.begin(),nums.end());
        return nums.size()!=s.size();
    }
};
```
