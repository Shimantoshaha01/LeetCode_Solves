# Problem No: 2333. Minimum Sum of Squared Difference(Medium)

**LINK:** [Click here](https://leetcode.com/problems/minimum-sum-of-squared-difference/description/?envType=daily-question&envId=2026-10-10)

```cpp
class Solution {
public:
    long long minSumSquareDiff(vector<int>& nums1, vector<int>& nums2, int k1,
                               int k2) {
        int n = nums1.size();
        long long k = (long long)k1 + k2;

        vector<long long> count(100005, 0);
        long long max_diff = 0;
        long long total_sum = 0;

        for (int i = 0; i <n ; i++) {
            long long diff = abs(nums1[i] - nums2[i]);
            count[diff]++;
            max_diff = max(max_diff, diff);
            total_sum += diff;
        }

        if (total_sum <= k)
            return 0;

        for (long long i = max_diff; i > 0; i--) {
            if (count[i] == 0)
                continue;

            long long reduce = min(k, count[i]);
            count[i] -= reduce;
            count[i - 1] += reduce;
            k -= reduce;
            if (k == 0)
                break;
        }

        long long ans = 0;
        for (long long i = 0; i <= max_diff; ++i) {
            if (count[i] > 0) {
                ans += count[i] * i * i;
            }
        }
        return ans;
    }
};
