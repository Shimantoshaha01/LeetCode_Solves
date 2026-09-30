# Problem NO: Rearrange Array by Removing Distinct Values(Easy)

```cpp
class Solution {
public:
    vector<int> rearrangeArray(vector<int>& nums) {
        vector<int> ans;
        map<int, int> temp;

        for (auto n : nums) {
            temp[n]++;
        }
        int n = nums.size();

        while (ans.size() < n) {
            for (auto& [a, b] : temp) {
                if (b > 0) {
                    ans.push_back(a);
                    b--;
                }
            }
        }
        return ans;
    }
};
