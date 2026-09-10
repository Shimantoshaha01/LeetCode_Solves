# Problem No:  257. Binary Tree Paths (Easy)

** Link: ** [CLick here](https://leetcode.com/problems/binary-tree-paths/description/)

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
public:
    void findans(TreeNode* node, vector<string>& ans, string temp) {
        if (!node)
            return;

        temp += to_string(node->val);

        if (!node->left && !node->right) {
            ans.push_back(temp);
            return;
        }

        findans(node->left, ans, temp + "->");
        findans(node->right, ans, temp + "->");
    }

    vector<string> binaryTreePaths(TreeNode* root) {
        vector<string> ans;
        if (root) {
            findans(root, ans, "");
        }
        return ans;
    }
};
