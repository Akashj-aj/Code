# Move Zeroes

Problem Link: https://leetcode.com/problems/move-zeroes/

## Simple Logic

Idea:
- Use two pointers: `i` and `j`.
- `j` scans the full array.
- `i` marks where the next non-zero should be placed.
- Whenever `nums[j] != 0`, swap `nums[i]` and `nums[j]`, then increment `i`.

Why this works:
- All non-zero elements get moved forward in their original order.
- Zeroes automatically shift to the end.
- Done in-place with `O(1)` extra space.

## Python

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        i=0
        for j in range(len(nums)):
            if nums[j]!=0:
                nums[i],nums[j]=nums[j],nums[i]
                i+=1
```

## C++

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
       int i=0;
       for (int j=0;j<nums.size();j++){
        if (nums[j]!=0){
            swap(nums[i],nums[j]);
            i++;
        }
       }
    }
};
```

## Learning Note

I got stuck on this problem at first.
My initial approach gave Time Limit Exceeded.
After seeing other solutions, I understood the correct two-pointer flow, and a little edit was needed to fix it.

Note: Same array, same logic, one pointer fix - suddenly LeetCode stopped being angry.
