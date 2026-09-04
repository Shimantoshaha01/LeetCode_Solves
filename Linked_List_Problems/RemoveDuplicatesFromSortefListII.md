# Problem No:  82. Remove Duplicates from Sorted List II(Medium)
** LINK: ** [ CLICK HERE ](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/description/?envType=study-plan-v2&envId=top-interview-150)

# Solution
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
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* curr = dummy;

        while (curr->next && curr->next->next) {
            if (curr->next->val == curr->next->next->val) {
                int duplicate = curr->next->val;
                while (curr->next && curr->next->val == duplicate)
                    curr->next = curr->next->next;
            } else
                curr = curr->next;
        }
        return dummy->next;
    }

};
