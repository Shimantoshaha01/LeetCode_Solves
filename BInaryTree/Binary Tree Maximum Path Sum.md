# Problem : 124. Binary Tree Maximum Path Sum (Hard)

** Link ** [Click here](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/?envType=study-plan-v2&envId=top-interview-150)

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
    int maxSum = INT_MIN;
    int solution(TreeNode* root) {
        if (root == nullptr)
            return 0;

        int left = max(solution(root->left),0);
        int right = max(solution(root->right),0);
        int maxans = root->val + left + right;

        maxSum = max(maxSum, maxans);

        return root->val + max(left, right);
    }

public:
    int maxPathSum(TreeNode* root) {
        solution(root);
        return maxSum;
    }
};
