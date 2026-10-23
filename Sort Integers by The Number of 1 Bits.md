# Problem No: 1356. Sort Integers by The Number of 1 Bits(Easy)
**Link:** [Click here](https://leetcode.com/problems/sort-integers-by-the-number-of-1-bits/description/)

```cpp
class Solution {
public:
    vector<int> sortByBits(vector<int>& arr) {
        auto comp = [](int a, int b) {
            int numa = __builtin_popcount(a);
            int numb = __builtin_popcount(b);
            if (numa == numb)
                return a < b;
            return numa < numb;
        };
        sort(arr.begin(), arr.end(), comp);

        return arr;
    }
};
