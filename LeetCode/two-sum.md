# Two Sum

## Python

Approach: Brute force using two nested loops to check every pair.

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n=len(nums)
        for i in range(n-1):
            for j in range(i+1,n):
                if nums[i]+nums[j]==target:
                    return [i,j]
        return []
```

## C++

Approach (simple):
- Go left to right in the array.
- For each number `nums[i]`, calculate `key = target - nums[i]`.
- Check if `key` was already seen before.
- If yes, return the previous index and current index.
- If no, store current number with its index.

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map <int,int> m;
        for (int i = 0; i < nums.size(); i++) {
            int key=target-nums[i]; 
            if(m.find(key)!=m.end()){
                return {m[key],i};
            } 
            m[nums[i]]=i;   
        }
    return {};
    }
};
```

How this part works:

```cpp
if(m.find(key)!=m.end()){
    return {m[key],i};
}
m[nums[i]]=i;
```

- `m` stores: number -> index
- `m.find(key) != m.end()` means: the required partner number is already in the map.
- So `return {m[key], i};` returns both indices of numbers that make the target.
- If not found, `m[nums[i]] = i;` stores current number for future elements.
