# Problem No: 2482. Difference Between Ones and Zeros in Row and Column( Medium)

**Link:** [Click here](https://leetcode.com/problems/difference-between-ones-and-zeros-in-row-and-column/)

```cpp
class Solution {
public:
    vector<vector<int>> onesMinusZeros(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();

        vector<int> onerows(m, 0);
        vector<int> onecol(n, 0);

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {

                if (grid[i][j] == 1) {
                    onerows[i]++;
                    onecol[j]++;
                }
            }
        }
        vector<vector<int>> diff(m, vector<int>(n, 0));

        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                diff[r][c] = 2 * onerows[r] + 2 * onecol[c] - m - n;
            }
        }

        return diff;
    }
};
