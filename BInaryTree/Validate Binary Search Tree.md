# Problem No : 98. Validate Binary Search Tree(Medium)

**LINK:** [Click here](https://leetcode.com/problems/validate-binary-search-tree/submissions/2147973353/)

# Solution is made using DFS

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
    bool checkvalid(TreeNode* node, TreeNode* minNode, TreeNode* maxNode) {
        if (!node)
            return true;
        if (minNode && node->val <= minNode->val)
            return false;
        if (maxNode && node->val >= maxNode->val)
            return false;
        return checkvalid(node->left, minNode, node) && checkvalid(node->right, node, maxNode);
    }

public:
    bool isValidBST(TreeNode* root) {
        return checkvalid(root, nullptr, nullptr);
    }
};
