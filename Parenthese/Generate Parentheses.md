# Problem No: 22. Generate Parentheses(Medium)

**Link:** [Click here](https://leetcode.com/problems/generate-parentheses/description/?envType=daily-question&envId=2026-10-02)
# Solution is made using Backtracking .
```cpp
class Solution {
private:
    void backtrack(int open, int close, int n, string& current,
                   vector<string>& result) {
        if (open == n && close == n) {
            result.push_back(current);
            return;
        }

        if (open < n) {
            current.push_back('(');
            backtrack(open + 1, close, n, current, result);
            current.pop_back();
        }

        if (close < open) {
            current.push_back(')');
            backtrack(open, close + 1, n, current, result);
            current.pop_back();
        }
    }

public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        string current = "";
        backtrack(0, 0, n, current, result);
        return result;
    }
};
