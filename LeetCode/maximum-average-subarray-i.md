# Maximum Average Subarray I

Problem Link: https://leetcode.com/problems/maximum-average-subarray-i/

## Python

Approach:
- Take the sum of the first `k` elements.
- Keep it as the current window sum and also as the current best sum.
- Move the window one step at a time:
- Add the next element.
- Remove the element that goes out of the window.
- Update the maximum sum.
- Return `max_sum / k`.

```python
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        sums=sum(nums[:k])
        res=sums
        for i in range(k,len(nums)):
            sums+=nums[i]-nums[i-k]
            res=max(res,sums)
        return res/k
```

## C++

Approach:
- Find the sum of the first window of size `k`.
- Store it in `sum` and `res`.
- For every next position:
- Add the new element entering the window.
- Remove the old element leaving the window.
- Update the best sum.
- Return `res / k`.

```cpp
class Solution {
public:
    double findMaxAverage(vector<int>& nums, int k) {

        double sum = 0;
        
        for(int i = 0; i < k; i++)
            sum += nums[i];

        double res = sum;

        for(int i = k; i < nums.size(); i++){
            sum += nums[i];
            sum -= nums[i-k];
            res = max(res, sum);
        }

        return res / k;
    }
};
```

## Learning Note

The main idea here was sliding window.
We keep the current sum of size `k`, then add the next element and remove the previous one.
That makes the update efficient instead of recalculating the full sum every time.

Note: The window keeps moving, and we just keep the math from doing unnecessary overtime.
