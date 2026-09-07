# Problem No: 146 - LRU CACHE (MEDIUM)

** Link ** [Click here](https://leetcode.com/problems/lru-cache/description/?envType=study-plan-v2&envId=top-interview-150)

# Solution

```cpp

class LRUCache {
private:
    struct Node {
        int key;
        int value;
        Node* prev;
        Node* next;

        Node(int k, int v) {
            key = k;
            value = v;
            prev = nullptr;
            next = nullptr;
        }
    };

    unordered_map<int, Node*> mp;

    Node* head;
    Node* tail;

    int capacity;

    void remove(Node* node) {
        node->prev->next = node->next;
        node->next->prev = node->prev;
    }

    void insertAtEnd(Node* node) {
        Node* previous = tail->prev;

        previous->next = node;
        node->prev = previous;

        node->next = tail;
        tail->prev = node;
    }

public:
    LRUCache(int capacity) {
        this->capacity = capacity;

        head = new Node(0, 0);
        tail = new Node(0, 0);

        head->next = tail;
        tail->prev = head;
    }

    int get(int key) {
        if (mp.find(key) == mp.end()) {
            return -1;
        }

        Node* node = mp[key];

        remove(node);
        insertAtEnd(node);

        return node->value;
    }

    void put(int key, int value) {
        if (mp.find(key) != mp.end()) {
            Node* node = mp[key];

            node->value = value;

            remove(node);
            insertAtEnd(node);

            return;
        }

        Node* newNode = new Node(key, value);

        mp[key] = newNode;

        insertAtEnd(newNode);

        if (mp.size() > capacity) {
            Node* lru = head->next;

            remove(lru);

            mp.erase(lru->key);

            delete lru;
        }
    }
};
