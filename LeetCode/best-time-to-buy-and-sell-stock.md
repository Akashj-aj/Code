# Best Time to Buy and Sell Stock

Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Python (with `max`)

Approach (simple):
- Keep track of the minimum price seen so far (`buyprice`).
- At each day, calculate possible profit: `current_price - buyprice`.
- Keep the maximum profit seen so far.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        buyprice=float("inf")
        profit=0
        for p in prices:
            if p<buyprice:
                buyprice=p
            profit=max(profit,p-buyprice)
        return profit
```

## Python (without `max`)

Approach (same logic):
- Update `buyprice` when a smaller value appears.
- Update `profit` only if current profit is bigger than old profit.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        buyprice=float("inf")
        profit=0
        for p in prices:
            if p<buyprice:
                buyprice=p
            if p-buyprice>profit:
                profit=p-buyprice
        return profit
```

## C++

Approach:
- Track lowest buy price till current day.
- Check best profit if sold today.
- Keep best answer in `profit`.

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buyprice=INT_MAX;
        int profit=0;
        for (int i=0;i<prices.size();i++){
            if (prices[i]<buyprice){
                buyprice=prices[i];
            }
            if (prices[i]-buyprice>profit){
                profit=prices[i]-buyprice;
            }

        }
        return profit;
    }
};
```

## Simple Logic Explanation

If I sell on day `i`, best buy day must be the minimum price before (or at) day `i`.
So instead of checking all pairs, I just carry:
- `buyprice` = minimum price so far
- `profit` = maximum `(current price - buyprice)` so far

That is why this works in one pass.

## Learning Note

I got stuck because I was overthinking the logic.
Then I understood: just keep the lowest `buyprice` so far and check profit for each day.

Note: I was planning full market analysis; problem only wanted one minimum and one maximum.
