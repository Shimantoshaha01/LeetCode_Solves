# Problem No: 32. Longest Valid Parentheses(Hard)

**Link:** [Click here](https://leetcode.com/problems/longest-valid-parentheses/description/?envType=daily-question&envId=2026-10-03)

```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        stack<int> sol;
        int ma = 0;
        sol.push(-1);
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(')
                sol.push(i);
            else {
                sol.pop();
                if (sol.empty())
                    sol.push(i);
                else {
                    ma = max(ma, i - sol.top());
                }
            }
        }
        return ma;
    }
};
