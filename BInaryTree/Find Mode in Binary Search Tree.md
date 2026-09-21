# Problem No: 501. Find Mode in Binary Search Tree(Easy)

**Link:** [Click here](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)



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
    int maxfre = 0;
    int currfre = 0;
    vector<int> modes;
    TreeNode* prev = nullptr;
    void inorder(TreeNode* node) {
        if (!node)
            return;
        inorder(node->left);

        if (prev && node->val == prev->val)
            currfre++;
        else {
            currfre = 1;
        }
        if (currfre > maxfre) {
            maxfre = currfre;
            modes.clear();
            modes.push_back(node->val);
        } else if (currfre == maxfre)
            modes.push_back(node->val);

        prev = node;
        inorder(node->right);
    }

public:
    vector<int> findMode(TreeNode* root) {
        inorder(root);
        return modes;
    }
};
