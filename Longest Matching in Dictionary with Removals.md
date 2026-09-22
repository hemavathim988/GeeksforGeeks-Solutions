## 01. Longest Matching in Dictionary with Removals

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-largest-word-in-dictionary2430/1)

### Problem Description

**Task:** Given a lowercase string s and a dictionary d[] containing lowercase words, find the longest word in the dictionary that can be obtained by deleting some characters from s without changing the order of the remaining characters.Note: If multiple words have the same maximum length, return the lexicographically smallest one. If no valid word exists, return an empty string.Examples : Input: d = ["ale", "apple", "monkey", "plea"], s = "abpcplea"Output: "apple" Explanation: After deleting "b", "c", "a" s became "apple" which is present in d.

#### Examples

##### Example 1

- **Input:**
```text
d = ["a", "b", "c"], s = "abpcplea"Output: "a"Explanation: After deleting "b", "p", "c", "p", "l", "e", "a" s became "a" which is present in d.Constraints:1 ≤ |s| ≤ 5 * 10⁵¹ ≤ n ≤ 10⁴, where n is the number of words in dictionary^1 ≤ m ≤ 100, where m is the length of word in dictionarys and all words in dictionary consist only of lowercase English letters.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s| + n × m × log|s|)
- **Expected Auxiliary Space Complexity:** O(|s|)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-22 07:27:31
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def findLongestWord(self, s, d):
        d.sort(key=lambda x: (-len(x), x))

        for word in d:
            if len(word) > len(s):
                continue

            pos = 0
            ok = True

            for ch in word:
                pos = s.find(ch, pos)

                if pos == -1:
                    ok = False
                    break

                pos += 1

            if ok:
                return word

        return ""
```

*Generated on: 9/22/2026, 7:28:08 AM*