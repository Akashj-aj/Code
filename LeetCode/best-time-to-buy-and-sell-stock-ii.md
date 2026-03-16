# Best Time to Buy and Sell Stock II

Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

## Simple Logic

Idea:
- Start from index `1`.
- Compare current day with previous day.
- If price is increasing, add that difference to profit.
- If price is decreasing, skip.

Why this works:
- We are collecting every small upward move.
- Adding all positive differences is same as buying at each local low and selling at each local high.

## Example Walkthrough

Input: `prices = [7,1,5,3,6,4]`

`i = 1` (compare `1` and `7`)
- Previous is bigger, no profit.
- `profit = 0`

`i = 2` (compare `5` and `1`)
- Increase found: `5 - 1 = 4`
- `profit = 4`

`i = 3` (compare `3` and `5`)
- Previous is bigger, no profit.
- `profit = 4`

`i = 4` (compare `6` and `3`)
- Increase found: `6 - 3 = 3`
- `profit = 4 + 3 = 7`

`i = 5` (compare `4` and `6`)
- Previous is bigger, no profit.
- `profit = 7`

Final answer: `7`

## Python

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit=0

        for i in range(1,len(prices)):
            if prices[i]>prices[i-1]:
                profit+=prices[i]-prices[i-1]
        return profit
```

## C++

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit=0;
        for(int i=1;i<prices.size();i++){
            if(prices[i]>prices[i-1]){
                profit+=prices[i]-prices[i-1];
            }
        }
        return profit;
    }
};
```

## Learning Note

I did not get this logic at first and got stuck while trying.
After seeing the solution, I understood the trick: only add positive day-to-day gains.

Note: I made it complicated for no reason, then the solution said: just add every profit when price goes up.