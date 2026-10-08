# Problem No: 564. Find the Closest Palindrome(Hard)

**Link:** [Click here](https://leetcode.com/problems/find-the-closest-palindrome/description/)

```cpp
class Solution {
private:
    
    long long createPalindrome(long long prefix, bool isEven) {
        long long result = prefix;
        if (!isEven) prefix /= 10; 
        
        while (prefix > 0) {
            result = result * 10 + (prefix % 10);
            prefix /= 10;
        }
        return result;
    }

public:
    string nearestPalindromic(std::string n) {
        int len = n.length();
        long long num = stoll(n);

        
        vector<long long> candidates;
        candidates.push_back((long long)pow(10, len - 1) - 1); 
        candidates.push_back((long long)pow(10, len) + 1);     

        
        int prefixLen = (len + 1) / 2;
        long long prefix = stoll(n.substr(0, prefixLen));

        
        for (int i : {-1, 0, 1}) {
            candidates.push_back(createPalindrome(prefix + i, len % 2 == 0));
        }

        
        long long closest = -1;
        long long minDiff = LLONG_MAX;

        for (long long cand : candidates) {
            if (cand == num) continue; 

            long long diff = abs(cand - num);
            if (diff < minDiff) {
                minDiff = diff;
                closest = cand;
            } else if (diff == minDiff) {
                closest = min(closest, cand); 
            }
        }

        return to_string(closest);
    }
};
