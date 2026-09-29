# Problem NO : 2101. Detonate the Maximum Bombs( Medium)

**Link:**[Click here](https://leetcode.com/problems/detonate-the-maximum-bombs/description/)

# Solution is made using DFS

```cpp
class Solution {
private:
    int dfs(int node, vector<vector<int>>& adj,vector<bool>& visited) {
        visited[node] = true;
        int count = 1;

        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                count += dfs(neighbor, adj, visited);
            }
        }

        return count;
    }

public:
    int maximumDetonation(vector<vector<int>>& bombs) {
        int n = bombs.size();
        vector<vector<int>> adj(n);

        for (int i = 0; i < n; i++) {
            long long x1 = bombs[i][0];
            long long y1 = bombs[i][1];
            long long r1 = bombs[i][2];

            for (int j = 0; j < n; j++) {
                if (i == j)
                    continue;

                long long x2 = bombs[j][0];
                long long y2 = bombs[j][1];

                long long dx = x2 - x1;
                long long dy = y2 - y1;

               long long  dist = dx * dx + dy * dy;

                if (dist <= r1 * r1)
                    adj[i].push_back(j);
            }
        }
        int detonated = 0;
        for (int i = 0; i < n; i++) {
            vector<bool> visited(n, false);
            int count = dfs(i, adj, visited);
            detonated = max(detonated, count);
            if (n == detonated)
                break;
        }
        return detonated;
    }
};

