## 01. Unoccupied Computers

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/unoccupied-computers-1646661078/1)

### Problem Description

**Task:** A cafe has n computers. The customer events are represented by a string s of uppercase English letters, where each distinct letter appears exactly twice:
The first occurrence denotes the customer's arrival.
The second occurrence denotes the customer's departure.
A customer is assigned a computer only if one is available at the time of arrival, otherwise the customer is rejected and does not use a computer.
Return the number of customers who could not be assigned a computer upon arrival.

#### Examples

##### Example 1

- **Input:**
```text
n = 3, s = "GACCBDDBAGEE"
```
- **Output:**
```text
1
```
- **Explanation:** Only D will not be able to get any computer. So the answer is 1.

##### Example 2

- **Input:**
```text
n = 1, s = "ABCBAC"
```
- **Output:**
```text
2
```
- **Explanation:** B and C will not be able to get any computers. So the answer is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Python)

- **Submitted:** 2026-09-06 20:28:55
- **Status:** Correct
- **Marks:** 0

```python
class Solution:
    def solve(self, n, s):
        seen = set()
        computers = set()
        answer = 0

        for ch in s:
            if ch not in seen:
                seen.add(ch)

                if len(computers) < n:
                    computers.add(ch)
                else:
                    answer += 1

            else:
                if ch in computers:
                    computers.remove(ch)

        return answer
```

#### Solution 2 (Python)

- **Submitted:** 2026-09-02 20:17:57
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def solve(self, n, s):
        seen = set()
        computers = set()
        answer = 0

        for ch in s:
            if ch not in seen:
                seen.add(ch)

                if len(computers) < n:
                    computers.add(ch)
                else:
                    answer += 1

            else:
                if ch in computers:
                    computers.remove(ch)

        return answer
```

*Generated on: 9/6/2026, 8:29:27 PM*