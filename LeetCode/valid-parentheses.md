# Valid Parentheses

Problem Link: https://leetcode.com/problems/valid-parentheses/

## Python

Approach:
- Use a stack to store opening brackets.
- Traverse the string.
- If the current character is an opening bracket, push it.
- If it is a closing bracket, check the top of the stack.
- If the stack is empty or the brackets do not match, return `False`.
- At the end, return `True` only if the stack is empty.

```python
class Solution:
    def isValid(self, s: str) -> bool:
        i=0
        a=[]
        for i in range(len(s)):
            if s[i]=='('or s[i]=='['or s[i]=='{':
                a.append(s[i])
            else:
                if not a:
                    return False
                top=a.pop()
                if s[i]==')'and top!='(':
                    return False
                if s[i]==']'and top!='[':
                    return False
                if s[i]=='}'and top!='{':
                    return False
        return len(a)==0
```

## C++

Approach:
- Use `stack<char>` to keep opening brackets.
- Push opening brackets into the stack.
- For closing brackets, check if stack is empty or if top does not match.
- If anything mismatches, return `false`.
- At the end, stack must be empty.

```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        for (char ch : s) {
            if (ch == '(' || ch == '[' || ch == '{') {
                st.push(ch);
            } else {
                if(st.empty()){
                    return false;
                }
                char top=st.top();
                st.pop();
                if(ch==')' && top!='(') return false;
                if(ch==']' && top!='[') return false;
                if(ch=='}' && top!='{') return false;

            }

    }
    return st.empty();
}
};
```

## Learning Note

In this problem, stack was the clear idea for handling brackets.
I did not really think of solving it in any other way.

Note: The moment brackets appeared, stack basically said, "leave this to me."
