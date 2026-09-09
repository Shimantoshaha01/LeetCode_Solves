# Problem No:  114. Flatten Binary Tree to Linked List(Medium)

** Link : ** [Click here](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/?envType=study-plan-v2&envId=top-interview-150)

# Solution is made using Recursion.
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
    TreeNode* prev = nullptr;
    void flatten(TreeNode* root) {
        if (root == nullptr)
            return ;

        flatten(root->right);
        flatten(root->left);

        root->right = prev;
        root->left = nullptr;

        prev = root;
    }
};
