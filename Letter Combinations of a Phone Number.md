# Problem No: 17. Letter Combinations of a Phone Number(Medium)

**Link:** [Click here](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

```cpp

class Solution {
private:
    vector<string> ans{"",     // 0
                       "",     // 1
                       "abc",  // 2
                       "def",  // 3
                       "ghi",  // 4
                       "jkl",  // 5
                       "mno",  // 6
                       "pqrs", // 7
                       "tuv",  // 8
                       "wxyz"};
    void solution(string& digits, int idx, string& current,
                  vector<string>& result) {
        if (idx == digits.length()) {
            result.push_back(current);
            return;
        }
        string letter = ans[digits[idx] - '0'];
        for (auto c : letter) {
            current.push_back(c);
            solution(digits, idx + 1, current, result);
            current.pop_back();
        }
    }

public:
    vector<string> letterCombinations(string digits) {
        string current = "";
        vector<string> result;
        if (digits.empty())
            return result;

        solution(digits, 0, current, result);
        return result;
    }
};
