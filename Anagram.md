## 01. Anagram

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/anagram-1587115620/1)

### Problem Description

**Task:** Given two non-empty strings s1 and s2, consisting only of lowercase English letters, determine whether they are anagrams of each other or not. Two strings are considered anagrams if they contain the same characters with exactly the same frequencies, regardless of their order.

#### Examples

##### Example 1

- **Input:**
```text
s1 = "geeks" s2 = "kseeg"Output: true Explanation: Both the string have same characters with same frequency. So, they are anagrams.
```

##### Example 2

- **Input:**
```text
s1 = "allergy", s2 = "allergyy" Output: false Explanation: Although the characters are mostly the same, s2 contains an extra 'y' character. Since the frequency of characters differs, the strings are not anagrams.
```

##### Example 3

- **Input:**
```text
s1 = "listen", s2 = "lists" Output: false Explanation: The characters in the two strings are not the same — some are missing or extra. So, they are not anagrams.
```

#### Constraints

- **1.** `1 ≤ s1.size(), s2.size() ≤ 105s1, s2 consists of lowercase English letters.`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n + m)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-06 20:24:41
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def areAnagrams(self, s1, s2):
       return sorted(s1)==sorted(s2)
```

*Generated on: 9/6/2026, 8:27:40 PM*