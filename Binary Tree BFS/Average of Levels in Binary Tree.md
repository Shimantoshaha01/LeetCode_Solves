# Problem No : 637. Average of Levels in Binary Tree (Easy)

** Link : ** [CLick here ](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/?envType=study-plan-v2&envId=top-interview-150)

# Solution is made using made BFS

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
    vector<double> averageOfLevels(TreeNode* root) {
        if (!root)
            return {};

        queue<TreeNode*> store;
        vector<double> ans;
        store.push(root);
        while(!store.empty()) {
            double n = store.size();
            double sum = 0;
            for (int i = 0; i < n; i++) {
                TreeNode* node = store.front();
                store.pop();
                if (node->left)
                    store.push(node->left);
                if (node->right)
                    store.push(node->right);
                sum += node->val;
            }
            ans.push_back((sum / n));
        }
        return ans;
    }
};
