# Problem No:  993. Cousins in Binary Tree(Easy)

**Link:** [Click here](https://leetcode.com/problems/cousins-in-binary-tree/description/)

# Solution made using DFS


```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left),
 * right(right) {}
 * };
 */
class Solution {
private:
    TreeNode* parent_x = nullptr;
    TreeNode* parent_y = nullptr;
    int depth_x = -1, depth_y = -1;
    void dfs(TreeNode* root, TreeNode* parent, int x, int y, int depth) {
        if (!root)
            return;
        if (root->val == x) {
            parent_x = parent;
            depth_x = depth;
        }
        if (root->val == y) {
            parent_y = parent;
            depth_y = depth;
        }
        if (depth_x != -1 && depth_y != -1)
            return;

        dfs(root->left, root, x, y, depth + 1);
        dfs(root->right, root, x, y, depth + 1);
    }

public:
    bool isCousins(TreeNode* root, int x, int y) {
        
        dfs(root, nullptr, x, y, 0) ;
        return (depth_x == depth_y) &&
            (parent_x != parent_y);
    }
};
