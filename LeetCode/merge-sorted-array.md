# Merge Sorted Array

Problem Link: https://leetcode.com/problems/merge-sorted-array/

## Python (with sort)

Approach:
- Put all elements of `nums2` into the empty part of `nums1`.
- Sort `nums1`.
- Since the problem allows modifying `nums1` in-place, this works.

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
     
       for i in nums2:
            nums1[m]=i
            m+=1
        nums1.sort()
```

## Python (without sort)

Approach:
- Start from the end of both valid parts of the arrays.
- Compare the last valid elements of `nums1` and `nums2`.
- Put the bigger one at the end of `nums1`.
- Move backward until all elements of `nums2` are placed.

```python
class Solution:
    def merge(self, nums1, m, nums2, n):
        i = m - 1
        j = n - 1
        k = m + n - 1

        while j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
```

## C++ (without sort)

Approach:
- Keep three pointers:
- `i` at the last valid element of `nums1`
- `j` at the last element of `nums2`
- `k` at the last position of `nums1`
- Compare from the back and place the bigger element at `k`.

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {

        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while(j >= 0){
            if(i >= 0 && nums1[i] > nums2[j]){
                nums1[k] = nums1[i];
                i--;
            }
            else{
                nums1[k] = nums2[j];
                j--;
            }
            k--;
        }
    }
};
```

## C++ (with sort)

Approach:
- Copy all values of `nums2` into the remaining part of `nums1`.
- Sort the full array.

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {

        for(int x : nums2){
            nums1[m] = x;
            m++;
        }

        sort(nums1.begin(), nums1.end());
    }
};
```

## Learning Note

The sort-based approach felt easier to me first, so I solved it that way.
I knew there was another approach without using sort, but I did not put extra effort into finding it on my own once the problem was already solved.
After seeing others' solutions, I understood how the backward three-pointer logic works.

Note: The problem was already solved with sort, so my brain politely declined unpaid extra work.
