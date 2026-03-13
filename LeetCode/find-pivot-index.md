# Find Pivot Index

Problem Link: https://leetcode.com/problems/find-pivot-index/

## Python

Approach:
- Find the total sum of the array.
- Keep a running `left` sum.
- For each index, calculate `right = total - left - nums[i]`.
- If `left == right`, that index is the pivot index.
- Otherwise, add `nums[i]` to `left` and continue.

```python
class Solution:
    def pivotIndex(self, nums):
        total = sum(nums)
        left = 0
        for i in range(len(nums)):
            right = total - left - nums[i]
            if left == right:
                return i
            left += nums[i]
        return -1
```

## C++

Approach:
- First calculate the total sum.
- Keep `left` as the running left-side sum.
- For each index, compute the right-side sum using `total - left - nums[i]`.
- If both sides are equal, return that index.

```cpp
class Solution {
public:
    int pivotIndex(vector<int>& nums) {

        int total = 0;
        for(int x : nums){
            total += x;
        }

        int left = 0;

        for(int i = 0; i < nums.size(); i++){
            int right = total - left - nums[i];

            if(left == right){
                return i;
            }

            left += nums[i];
        }

        return -1;
    }
};
```

## Learning Note

The approach that came to my mind first did not work.
So as usual, I checked others' solutions, understood the logic, and realized the actual approach was simpler than what I was trying.

Note: I was expecting some twist, but the problem just wanted left sum, right sum, and less drama.
