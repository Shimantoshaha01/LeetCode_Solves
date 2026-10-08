# Problem No : 2116. Check if a Parentheses String Can Be Valid(Medium)
**Link:** [CLick here](https://leetcode.com/problems/check-if-a-parentheses-string-can-be-valid/description/)


```cpp
class Solution {
public:
    bool canBeValid(string s, string locked) {
        if (locked.length() % 2 != 0)
            return false;
        int balance = 0;

        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(' || locked[i] == '0')
                balance++;
            else
                balance--;
            if (balance < 0)
                return false;
        }
         balance=0;
        for (int i = s.length() - 1; i >= 0; i--) {
            if (s[i] == ')' || locked[i] == '0')
                balance++;
            else
                balance--;
            if (balance < 0)
                return false;
        }
        return true;
    }
};
