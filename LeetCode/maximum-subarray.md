# Maximum Subarray

Problem Link: https://leetcode.com/problems/maximum-subarray/

## Python

Approach (Kadane's idea, simple):
- Keep adding numbers into `cur_sum`.
- Track the best sum in `max_sum`.
- If running sum becomes negative, reset it to `0` and start fresh from next element.

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

Note:
- I first wrote cur_sum < max_sum, like smaller sum should be the max, and honestly I donâ€™t know why I did that. Then I fixed it: cur_sum > max_sum

## C++

Approach (same idea):
- Add current element to `cur_sum`.
- Update answer when `cur_sum` is better.
- If `cur_sum` goes below 0, reset it because a negative running sum only hurts future subarrays.

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max_sum=INT_MIN;
        int cur_sum=0;
        for (int i=0;i<nums.size();i++){
            cur_sum+=nums[i];
            if(max_sum<cur_sum){
                max_sum=cur_sum;
            }
            if (cur_sum<0){
                cur_sum=0;
            }
            
        }
        return max_sum;
    }
};
```

Why do we need this?

```cpp
if (cur_sum<0){
    cur_sum=0;
}
```

Simple reason:
- If your running sum is negative, carrying it forward will reduce the next total.
- Better to drop that negative baggage and start new from the next index.

Note: Negative running sum helps no one; reset it and move on.
