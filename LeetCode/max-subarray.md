# Maximum Subarray

## Python

Approach: Kadane's Algorithm (track current running sum and best sum seen so far).

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        max_sum=float('-inf')
        cur_sum=0
        for i in nums:
            cur_sum+=i
            if cur_sum>max_sum:
                max_sum=cur_sum
            if cur_sum<0:
                cur_sum=0
        return max_sum
```

## C++

Approach: Same Kadane idea. Update `max_sum` first, then reset `cur_sum` if it becomes negative.

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max_sum = INT_MIN;
        int cur_sum = 0;

        for (int i = 0; i < nums.size(); i++) {
            cur_sum += nums[i];

            if (cur_sum > max_sum) {
                max_sum = cur_sum;
            }

            if (cur_sum < 0) {
                cur_sum = 0;
            }
        }

        return max_sum;
    }
};
```

## Why `cur_sum > max_sum`?

- `cur_sum` = sum of current subarray we are building.
- `max_sum` = best subarray sum found till now.
- If `cur_sum > max_sum`, we found a better answer, so we update `max_sum`.

## Why reset when `cur_sum < 0`?

```cpp
if (cur_sum < 0) {
    cur_sum = 0;
}
```

- A negative running sum hurts any future subarray.
- If we keep a negative prefix, adding future numbers gives smaller total.
- So we drop it and restart from next index.

Simple idea: negative baggage is never helpful for maximizing sum.
