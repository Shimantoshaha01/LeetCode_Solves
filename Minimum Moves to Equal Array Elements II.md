# Problem No: 462. Minimum Moves to Equal Array Elements II(Median)

**Link:** [CLick here]https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/description/)

```cpp
class Solution {
public:
    int minMoves2(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int median = nums[nums.size() / 2];

        int ans = 0;

        for (auto num : nums) {
            ans += abs(num - median);
        }
        return ans;
    }
};
