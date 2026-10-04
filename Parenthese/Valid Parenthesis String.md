# Problem NO: 678. Valid Parenthesis String(Medium)

**Link:** [Click here](https://leetcode.com/problems/valid-parenthesis-string/description/?envType=daily-question&envId=2026-10-04)
```cpp
class Solution {
public:
    bool checkValidString(string s) {
        stack<int> open;
        stack<int> star;

        for (int i = 0; i < s.length(); i++) {
            char c = s[i];
            if (c == '(') {
                open.push(i);
            } else if (c == '*') {
                star.push(i); 
            } else {
                if (!open.empty())
                    open.pop();
                else if (!star.empty())
                    star.pop();
                else
                    return false;
            }
        }

        
        while (!open.empty() && !star.empty()) {
            if (open.top() > star.top()) {
                return false; 
            }
            open.pop();
            star.pop();
        }

        
        return open.empty();
    }
};
