# Two Sum II - Input Array Is Sorted

Problem Link: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

## Python

Approach:
- Since the array is sorted, use two pointers.
- Keep `left` at the start and `right` at the end.
- Compute the current sum.
- If the sum is equal to target, return the 1-based indices.
- If the sum is smaller than target, move `left` forward.
- If the sum is greater than target, move `right` backward.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        left=0
        right=len(nums)-1

        while left<right:
            csum=nums[left]+nums[right]
            if csum==target:
                return [left+1,right+1]
            elif csum<target:
                left+=1
            else:
                right-=1
```

## C++

Approach:
- Use two pointers because the array is already sorted.
- Start one pointer from the left and one from the right.
- If current sum is too small, move left pointer.
- If current sum is too large, move right pointer.
- When sum matches target, return the 1-based indices.

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left=0;int right=numbers.size()-1;
        while(left<right){
            int csum= numbers[left] + numbers[right];
            if (csum==target){
                return {left+1,right+1};
            }
            else if (csum<target){
                left++;
            }
            else{
                right--;
            }
        }
        return {-1,-1};
    }
};
```

## Learning Note

I understood that since the array is sorted, using two pointers makes more sense than checking every pair.
The sum tells us directly which pointer needs to move, so the logic becomes simple.

Note: The array was already sorted and basically handing out hints, so brute force had no business staying.
