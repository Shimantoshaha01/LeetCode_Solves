# Problem No: 200. Number of Islands(Medium)

**Link:** [Click here](https://leetcode.com/problems/number-of-islands/description/?envType=study-plan-v2&envId=top-interview-150)

# Solution is made using DFS.


```cpp
class Solution {
private:
    void dfs(vector<vector<char>>& grid, int i, int j, int row, int col) {
        if (i < 0 || i >= row || j < 0 || j >= col || grid[i][j] == '0')
            return;
        grid[i][j]='0';

        dfs(grid, i-1, j, row, col);
        dfs(grid, i+1, j, row, col);
        dfs(grid, i, j-1, row, col);
        dfs(grid, i, j+1, row, col);
    }

public:
    int numIslands(vector<vector<char>>& grid) {
        if (grid.empty() || grid[0].empty())
            return 0;
        int row = grid.size();
        int col = grid[0].size();
        int island = 0;
        for (int i = 0; i < row; i++) {
            for (int j = 0; j < col; j++) {
                if (grid[i][j] == '1') {
                    island++;
                    dfs(grid, i, j, row, col);
                }
            }
        }
        return island;
    }
};
