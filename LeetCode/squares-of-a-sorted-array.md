# Squares of a Sorted Array

Problem Link: https://leetcode.com/problems/squares-of-a-sorted-array/

## Python (normal)

Approach:
- Traverse the array and square every number.
- Store all squared values in a new list.
- Sort that list because squaring negative numbers can disturb the order.
- Return the sorted result.

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        result = []
        for i in nums:
            result.append(i * i)
        result.sort()
        return result
```

## Python (two pointers)

Approach:
- Since the array is sorted, the largest square can come from either end.
- Use `left` at the beginning and `right` at the end.
- Compare `abs(nums[left])` and `abs(nums[right])`.
- Put the bigger square at the current index in `res`.
- Move that pointer and continue filling `res`.

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        res = [0] *len(nums)
        left = 0
        right = len(nums) - 1

        for i in range(len(nums) - 1, -1, -1):
            if abs(nums[left]) > abs(nums[right]):
                res[i] = nums[left] ** 2
                left += 1
            else:
                res[i] = nums[right] ** 2
                right -= 1
        
        return res
```

## C++ (normal)

Approach:
- Square every element and store it in a new vector.
- Sort the vector because the squared values may not stay in sorted order.
- Return the sorted vector.

```cpp
class Solution { 
public:
    vector<int> sortedSquares(vector<int>& nums) {
        vector <int> result;
        for (int i=0;i<nums.size();i++){
            result.push_back(nums[i] * nums[i]);
        }
        sort(result.begin(), result.end());
        return result;
    }
};
```

## C++ (two pointers)

Approach:
- Same as Python logic.

```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        vector<int> res(nums.size(), 0);
        int left = 0;
        int right = nums.size() - 1;

        for (int i = nums.size() - 1; i >= 0; i--) {
            if (abs(nums[left]) > abs(nums[right])) {
                res[i] = nums[left] * nums[left];
                left++;
            } else {
                res[i] = nums[right] * nums[right];
                right--;
            }
        }
        return res;        
    }
};
```

## Learning Note

I got the normal method first, where I square everything and sort it.
Then I understood that sorting makes the time complexity higher.
After looking at others' solutions, I got the two-pointer idea because I was not in the mood to think more.

Note: My solution was working peacefully until time complexity entered the chat.

