# Problem No : 542. 01 Matrix(Medium)

**Link:**[Click here](https://leetcode.com/problems/01-matrix/description/)

# Solution is made using DP


```cpp
class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& mat) {
        int row = mat.size();
        int col = mat[0].size();
        int tot = row + col;

        vector<vector<int>> dist(row, vector<int>(col, tot));

        for (int r = 0; r < row; r++) {
            for (int c = 0; c < col; c++) {
                if (mat[r][c] == 0)
                    dist[r][c] = 0;
                else {
                    if (r > 0) {
                        dist[r][c] = min(dist[r][c], dist[r - 1][c] + 1);
                    }
                    if (c > 0) {
                        dist[r][c] = min(dist[r][c], dist[r][c - 1] + 1);
                    }
                }
            }
        }

        for (int r = row - 1; r >= 0; r--) {
            for (int c = col - 1; c >= 0; c--) {
                if (r < row - 1) {
                    dist[r][c] = min(dist[r][c], dist[r + 1][c] + 1);
                }
                if (c < col - 1)
                    dist[r][c] = min(dist[r][c], dist[r][c + 1] + 1);
            }
        }

        return dist;
    }
};
