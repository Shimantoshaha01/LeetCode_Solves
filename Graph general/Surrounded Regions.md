# Problem No : 130. Surrounded Regions( Medium)

**Link:** [Click here](http://leetcode.com/problems/surrounded-regions/description/)

# Solution is made using DFS


```cpp
#include <vector>

class Solution {
private:
    void dfs(std::vector<std::vector<char>>& board, int r, int c, int rows, int cols) {
        if (r < 0 || r >= rows || c < 0 || c >= cols || board[r][c] != 'O') {
            return;
        }

        board[r][c] = 'E';

        dfs(board, r + 1, c, rows, cols);
        dfs(board, r - 1, c, rows, cols);
        dfs(board, r, c + 1, rows, cols);
        dfs(board, r, c - 1, rows, cols);
    }

public:
    void solve(std::vector<std::vector<char>>& board) {
        if (board.empty() || board[0].empty()) return;

        int rows = board.size();
        int cols = board[0].size();

        for (int r = 0; r < rows; ++r) {
            if (board[r][0] == 'O') dfs(board, r, 0, rows, cols);
            if (board[r][cols - 1] == 'O') dfs(board, r, cols - 1, rows, cols);
        }

        for (int c = 0; c < cols; ++c) {
            if (board[0][c] == 'O') dfs(board, 0, c, rows, cols);
            if (board[rows - 1][c] == 'O') dfs(board, rows - 1, c, rows, cols);
        }

        for (int r = 0; r < rows; ++r) {
            for (int c = 0; c < cols; ++c) {
                if (board[r][c] == 'O') {
                    board[r][c] = 'X';
                } else if (board[r][c] == 'E') {
                    board[r][c] = 'O';
                }
            }
        }
    }
};
