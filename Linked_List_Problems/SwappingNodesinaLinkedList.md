#Problem No:1721. Swapping Nodes in a Linked List(Medium)
**Link:** [Click Here](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/)

##Solution


```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* swapNodes(ListNode* head, int k) {
        ListNode* start = head;
        ListNode* end = head;

        for (int i = 0; i < k - 1; i++) {
            start = start->next;
        }
        ListNode* finale = start;
        while (start->next) {
            start = start->next;
            end = end->next;
        }
        swap(finale->val, end->val);

        return head;
    }
};
