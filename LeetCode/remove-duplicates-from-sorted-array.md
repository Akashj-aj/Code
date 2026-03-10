# Remove Duplicates from Sorted Array

Problem Link: https://leetcode.com/problems/remove-duplicates-from-sorted-array/

## Python

Approach:
- Use two pointers: `i` for the position of the last unique element and `j` for scanning.
- If `nums[j]` is different from `nums[i]`, move `i` forward and place the new unique value there.
- Return `i + 1` because that is the count of unique elements.

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i=0
        for j in range (1,len(nums)):
            if nums[j]!=nums[i]:
                i+=1
                nums[i]=nums[j]
        return i+1
```

## C++

Approach:
- If the array is empty, return `0`.
- Use `i` to track the position of the last unique element.
- Use `j` to scan the array.
- When `nums[j]` is different from `nums[i]`, move `i` forward and place `nums[j]` there.
- Return `i + 1` as the number of unique elements.

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i=0;
        if (nums.size()==0){
            return 0;
        }
        for (int j=1;j<nums.size();j++){
            if (nums[j]!=nums[i]){
                i++;
                nums[i]=nums[j];
            }
        }
        return i+1;
    }
};
```

## Learning Note

I got confused at first about what to return, because apparently returning the unique count was too normal for my brain.
After looking at others' solutions, I understood that `k` just means the number of unique elements, and only those need to stay in front.

Note: I thought the entire array needed a full makeover, but LeetCode only cared about the first `k` elements.
