# Problem  NO : 20. Valid Parentheses(Easy)

**Link:** [CLick here](https://leetcode.com/problems/valid-parentheses/?envType=daily-question&envId=2026-10-01)



```cpp
class Solution {
public:
    bool isValid(string s) {

        stack<char> sol;
        for (char c : s) {
            if (c == '(' || c == '[' || c == '{') {
                sol.push(c);
            } else {
                if (sol.empty())
                    return false;
                char top = sol.top();
                sol.pop();
                if (c == ')' && top != '(')
                    return false;
                if (c == ']' && top != '[')
                    return false;
                if (c == '}' && top != '{')
                    return false;
            }
        }
        return sol.empty();
    }
};
