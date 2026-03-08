# Valid Palindrome

Problem Link: https://leetcode.com/problems/valid-palindrome/

## Python (`isalnum`)

Approach:
- Build a cleaned string with only alphanumeric characters.
- Convert everything to lowercase.
- Check if it equals its reverse.

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        result=""
        for ch in s:
            if ch.isalnum():
                result+=ch.lower()
        return result==result[::-1]
```

## Python (without `isalnum`)

Approach:
- Use regex to remove non-alphanumeric characters.
- Convert to lowercase.
- Compare with reversed string.

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub('[^a-zA-Z0-9]', '', s).lower()
        return s == s[::-1]
```

## C++

Approach:
- Build `result` with only alphanumeric characters.
- Convert uppercase letters to lowercase.
- Compare from both ends.

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        string result;
        for (char c : s) {
            if (isalnum(c)) {
                if(isupper(c))
                {
                    result+=tolower(c);
                }
                else{
                    result+=c;
                }
            }
        }
        int i=0;int j=result.size()-1;
        for(i=0;i<result.size();i++){
            if(result[i]!=result[j]){
                return false;
            }
            j--;
        }
        return true;
    }
};
```

## Learning Note

I did not struggle much in this problem.
Once the string is cleaned and lowercased, palindrome check is straightforward.

Note: For once, my first logic worked without drama.
