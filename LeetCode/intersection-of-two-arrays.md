# Intersection of Two Arrays

Problem Link: https://leetcode.com/problems/intersection-of-two-arrays/

## Python (basic)

Approach:
- Traverse `nums1`.
- If element exists in `nums2` and not already in `result`, add it.
- Return unique common elements.

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        result=[]
        for i in nums1:
            if (i in nums2) and (i not in result):
                result.append(i)
        return result
```

## Python (set)

Approach:
- Convert both arrays to sets.
- Use set intersection.
- Convert back to list.

```python
class Solution:
    def intersection(self, nums1: list[int], nums2: list[int]) -> list[int]:
        return list(set(nums1) & set(nums2))
```

## C++ (brute force)

Approach:
- Compare every element of `nums1` with every element of `nums2`.
- Before inserting into result, check if already present.

```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        vector<int> result;
        for(int i = 0; i < nums1.size(); i++){
            for(int j = 0; j < nums2.size(); j++){
                if(nums1[i] == nums2[j]){
                    bool found = false;
                    for(int k = 0; k < result.size(); k++){
                        if(result[k] == nums1[i]){
                            found = true;
                            break;
                        }
                    }
                    if(!found){
                        result.push_back(nums1[i]);
                    }
                }

            }
        }

        return result;
    }
};
```

## C++ (set)

Approach:
- Put `nums1` values in set `s`.
- Traverse `nums2`, if found in `s`, insert into `result` set.
- Convert result set to vector.

```cpp
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        
        set<int> s(nums1.begin(), nums1.end());
        set<int> result;

        for(int x : nums2){
            if(s.count(x)){
                result.insert(x);
            }
        }

        return vector<int>(result.begin(), result.end());
    }
};
```

## Learning Note

I got a little stuck in the C++ logic for handling uniqueness in the result.
After comparing brute force and set-based approach, it became clear.

Note: Python set solution looked easy, C++ made me earn it.
