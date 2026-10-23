# Problem No: 3011. Find if Array Can Be Sorted(Medium)

**Link:** [Click here](https://leetcode.com/problems/find-if-array-can-be-sorted/description/)

```cpp
class Solution {
public:
    bool canSortArray(vector<int>& nums) {

        int n = nums.size();
        int currmax = nums[0];
        int currmin = nums[0];
        int prevmax = -1;
        int prev_set_bits = __builtin_popcount(nums[0]);

        for (int i = 1; i < n; i++) {
            int curr_set_bits = __builtin_popcount(nums[i]);
            if (prev_set_bits == curr_set_bits) {
                currmin = min(currmin, nums[i]);
                currmax = max(currmax, nums[i]);
            } else {
                if (currmin < prevmax)
                    return false;
                else {
                    prevmax = currmax;
                    currmin = nums[i];
                    currmax = nums[i];
                    prev_set_bits = curr_set_bits;
                }
            }
        }
        return currmin >= prevmax;
    }
};
