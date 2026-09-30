# Problem No:  Maximum Equal Adjacent Pairs After at Most One Replacement(Medium)


```cpp
class Solution {
public:
    int maxEqualAdjacentPairs(vector<int>& nums) {
        int n = nums.size();
        int base = 0;

        map<pair<int, int>, int> ans;

        int max_gain = 0;

        for (int i = 0; i < n - 1; i++) {
            int a = nums[i]; int b = nums[i + 1];

            if (a == b)
                base++;
            else {
                int u = min(a, b);
                int v = max(a, b);

                ans[{u, v}]++;
                max_gain = max(max_gain, ans[{u, v}]);
            }
        }
        return max_gain + base;
    }
};
