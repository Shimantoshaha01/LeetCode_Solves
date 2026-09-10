# Problem No:  Sum Root to Leaf Numbers (Medium)
** Link : ** [CLick here](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/?envType=study-plan-v2&envId=top-interview-150)
# Solution : Using dfs .

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
    int ans(TreeNode* node, int way) {
        if (!node)
            return 0;
        way = way * 10 + node->val;
        if (!node->left && !node->right)
            return way;
        return ans(node->left, way) + ans(node->right, way);
    }

public:
    int sumNumbers(TreeNode* root) { return ans(root, 0); }
};
