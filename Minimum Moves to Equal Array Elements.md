# Problem No: 453. Minimum Moves to Equal Array Elements(Medium)

**Link:** [Click here](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/description/?envType=daily-question&envId=2026-11-01)


```cpp
class Solution {
public:
    int minMoves(vector<int>& nums) {
        int min_val = *min_element(nums.begin(), nums.end());
        int ans = 0;

        for (auto num : nums) {
            ans += (num - min_val);
        }
        return ans;
    }
};
