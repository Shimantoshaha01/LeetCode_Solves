# Problem No : 61-Rotate List
** Link : ** [Click here](https://leetcode.com/problems/rotate-list/description/?envType=study-plan-v2&envId=top-interview-150)

```cpp



class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {

        if (!head || !head->next || k == 0)
            return head;

        int n = 1;
        ListNode* tail = head;

        while (tail->next) {
            tail = tail->next;
            n++;
        }

        k %= n;

        if (k == 0)
            return head;

        tail->next = head;  // circular

        ListNode* newTail = head;

        for (int i = 0; i < n - k - 1; i++) {
            newTail = newTail->next;
        }

        ListNode* newHead = newTail->next;

        newTail->next = nullptr;

        return newHead;
    }
};
