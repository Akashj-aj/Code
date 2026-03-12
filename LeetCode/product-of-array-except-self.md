# Product of Array Except Self

Problem Link: https://leetcode.com/problems/product-of-array-except-self/

## Python

Approach:
- Create an output array filled with `1`.
- In the first pass, store the product of all elements to the left of each index.
- In the second pass, multiply by the product of all elements to the right of each index.
- Final `output[i]` becomes product of all elements except `nums[i]`.

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        output = [1] * len(nums)
        
        left = 1
        for i in range(len(nums)):
            output[i] *= left
            left *= nums[i]
        
        right = 1
        for i in range(len(nums) - 1, -1, -1):
            output[i] *= right
            right *= nums[i]
    
        return output
```

## Python (prefix and suffix arrays)

Approach:
- Build a `prefix` array where each position stores product of all elements before it.
- Build a `suffix` array where each position stores product of all elements after it.
- Multiply `prefix[i]` and `suffix[i]` to get the answer for index `i`.

```python
class Solution:
    def productExceptSelf(self, nums):
        n = len(nums)

        prefix = [0] * n
        suffix = [0] * n
        ans = [0] * n

        prefix[0] = 1
        for i in range(1, n):
            prefix[i] = prefix[i-1] * nums[i-1]

        suffix[n-1] = 1
        for i in range(n-2, -1, -1):
            suffix[i] = suffix[i+1] * nums[i+1]

        for i in range(n):
            ans[i] = prefix[i] * suffix[i]

        return ans
```

## C++

Approach:
- Initialize `output` with `1`s.
- First loop stores left product for every index.
- Second loop multiplies right product into the same output array.
- This avoids using division.

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> output(nums.size(), 1);

        int left = 1;
        for (int i = 0; i < nums.size(); i++) {
            output[i] *= left;
            left *= nums[i];
        }

        int right = 1;
        for (int i = nums.size() - 1; i >= 0; i--) {
            output[i] *= right;
            right *= nums[i];
        }

        return output;        
    }
};
```

## C++ (prefix and suffix arrays)

Approach:
- Build a `prefix` array where each position stores product of elements before it.
- Build a `suffix` array where each position stores product of elements after it.
- Multiply `prefix[i]` and `suffix[i]` to get the final answer for each index.

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {

        int n = nums.size();

        vector<int> prefix(n);
        vector<int> suffix(n);
        vector<int> ans(n);

        prefix[0] = 1;
        for(int i = 1; i < n; i++){
            prefix[i] = prefix[i-1] * nums[i-1];
        }

        suffix[n-1] = 1;
        for(int i = n-2; i >= 0; i--){
            suffix[i] = suffix[i+1] * nums[i+1];
        }

        for(int i = 0; i < n; i++){
            ans[i] = prefix[i] * suffix[i];
        }

        return ans;
    }
};
```

## Learning Note

This problem felt hard to me.
I tried solving it, but I could not figure out the logic properly.
After getting tired, I checked others' solutions, copied the code, and then tried to understand the explanation.
Even that explanation was not easy to follow without visualizing what the left and right products were doing.

Note: First the problem was hard, then even the explanation acted like it needed its own explanation.
