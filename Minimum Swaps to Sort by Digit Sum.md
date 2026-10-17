# Problem No: 3551. Minimum Swaps to Sort by Digit Sum(Medium)

**Link:** [Click here](https://leetcode.com/problems/minimum-swaps-to-sort-by-digit-sum/description/?envType=daily-question&envId=2026-10-17)


```cpp

class Solution {
private:
    int breaknumbers(int n) {
        int ans = 0;

        while (n > 0) {
            ans += n % 10;
            n /= 10;
        }

        return ans;
    }

public:
    int minSwaps(vector<int>& nums) {
        int n = nums.size();

        
        vector<pair<int, int>> arr;

        for (int i = 0; i < n; i++) {
            arr.push_back({nums[i], i});
        }


        sort(arr.begin(), arr.end(), [&](auto a, auto b) {
            int sumA = breaknumbers(a.first);
            int sumB = breaknumbers(b.first);

            if (sumA != sumB)
                return sumA < sumB;

            return a.first < b.first;
        });

        vector<bool> visited(n, false);
        int swaps = 0;

        for (int i = 0; i < n; i++) {
            if (visited[i] || arr[i].second == i)
                continue;

            int cycleSize = 0;
            int j = i;

            while (!visited[j]) {
                visited[j] = true;
                j = arr[j].second;
                cycleSize++;
            }

            if (cycleSize > 1)
                swaps += cycleSize - 1;
        }

        return swaps;
    }
};
