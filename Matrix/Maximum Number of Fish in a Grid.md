# Problem No: 2658. Maximum Number of Fish in a Grid(Medium)

**Link:** [Click here](https://leetcode.com/problems/maximum-number-of-fish-in-a-grid/description/)

# Solution is made using DFS.
```
class Solution {
private:
    int dfs(vector<vector<int>>& grid, int r, int c, int row, int col) {
        if (r < 0 || r >= row || c < 0 || c >= col || grid[r][c] == 0)
            return 0;
        int maxsum = grid[r][c];
        grid[r][c] = 0;
        maxsum += dfs(grid, r - 1, c, row, col);
        maxsum += dfs(grid, r + 1, c, row, col);
        maxsum += dfs(grid, r, c - 1, row, col);
        maxsum += dfs(grid, r, c + 1, row, col);
        return maxsum;
    }

public:
    int findMaxFish(vector<vector<int>>& grid) {
        int row = grid.size();
        int col = grid[0].size();
        int maxsum = 0;

        for (int r = 0; r < row; r++) {
            for (int c = 0; c < col; c++) {
                if (grid[r][c] > 0) {
                    int temp = dfs(grid, r, c, row, col);
                    maxsum = max(temp, maxsum);
                }
            }
        }
        return maxsum;
    }
};
