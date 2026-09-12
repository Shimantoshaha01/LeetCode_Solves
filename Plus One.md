# Problem No : 66 -Plus one (Easy)

** Link : ** [Click here](https://leetcode.com/problems/plus-one/)

```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        // move backwards
        for (int i = digits.size() - 1; i >= 0; i--) {
            int num = digits[i] + 1;
            if (num == 10 && i != 0) {
                digits[i] = 0;
            }
            else {
                digits[i] = num;
                break;
            }
        }
        if (digits[0] == 10) {
            digits[0] = 1;
            digits.push_back(0);
        }
        return digits;
}
};
