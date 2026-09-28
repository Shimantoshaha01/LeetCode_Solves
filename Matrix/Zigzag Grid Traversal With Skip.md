# Problem No : 3417. Zigzag Grid Traversal With Skip(Easy)

**Link:** [Click here]https://leetcode.com/problems/zigzag-grid-traversal-with-skip/description/)

```cpp
class Solution {
public:
    vector<int> zigzagTraversal(vector<vector<int>>& grid) {
        int row = grid.size();
        int col = grid[0].size();
        vector<int> ans;
        bool keep = true;
        for (int r = 0; r < row; r++) {
            if (r % 2 == 0) {
                for (int c = 0; c < col; c++) {
                    if (keep) {
                        ans.push_back(grid[r][c]);
                    }
                    keep = !keep;
                }
            } else {
                for (int c = col - 1; c >= 0; c--) {
                    if (keep) {
                        ans.push_back(grid[r][c]);
                    }
                    keep = !keep;
                }
            }
        }

        return ans;
    }
};
