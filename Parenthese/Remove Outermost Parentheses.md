# Problem No: 1021. Remove Outermost Parentheses(Easy)

**Link:** [Click here](https://leetcode.com/problems/remove-outermost-parentheses/description/?envType=daily-question&envId=2026-10-08)

```cpp
class Solution {
public:
    string removeOuterParentheses(string s) {
        string ans = "";
        int opened = 0;
        for (char c : s) {
            if (c == '(') {
                if (opened > 0)
                    ans += c;
                opened++;
            } else {
                opened--;
                if (opened > 0)
                    ans += c;
            }
        }
        return ans;
    }
};
