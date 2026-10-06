# Problem No: 921. Minimum Add to Make Parentheses Valid(Medium)
**Link:** [Click here](https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/description/?envType=daily-question&envId=2026-10-06)

```cpp
class Solution {
public:
    int minAddToMakeValid(string s) {
        int open = 0, add = 0;
        for (char c : s) {
            if (c == '(') {
                open++;
            } else {
                if (open > 0)
                    open--;
                else
                    add++;
            }
        }
        return add + open;
    }
};
