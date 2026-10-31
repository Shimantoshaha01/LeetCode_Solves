# Problem No: 3665. Twisted Mirror Path Count(Medium)

**Link:** [Click here](https://leetcode.com/problems/twisted-mirror-path-count/description/?envType=daily-question&envId=2026-10-31)

```cpp
class Solution {
public:
    int uniquePaths(vector<vector<int>>& grid) {
        const int MOD = 1e9 + 7;

        int m = grid.size();
        int n = grid[0].size();

        vector<vector<int>> right(m, vector<int>(n, 0));
        vector<vector<int>> down(m, vector<int>(n, 0));

        int ans = 0;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {

                if (grid[i][j] == 1) {
                    if (i + 1 < m) {
                        down[i + 1][j] = (down[i + 1][j] + right[i][j]) % MOD;
                    }

                    if (j + 1 < n) {
                        right[i][j + 1] = (right[i][j + 1] + down[i][j]) % MOD;
                    }
                } 
                else {
                    int ways = (right[i][j] + (long long)down[i][j]) % MOD;

                    if (i == 0 && j == 0) {
                        ways = 1;
                    }

                    if (i == m - 1 && j == n - 1) {
                        ans = ways;
                    } else {
                        if (j + 1 < n) {
                            right[i][j + 1] = (right[i][j + 1] + ways) % MOD;
                        }

                        if (i + 1 < m) {
                            down[i + 1][j] = (down[i + 1][j] + ways) % MOD;
                        }
                    }
                }
            }
        }

        return ans;
    }
};
