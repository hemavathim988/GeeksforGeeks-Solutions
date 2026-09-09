## 01. Max Digit Sum Number in 1 to n

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/biggest-integer-having-maximum-digit-sum1704/1)

### Problem Description

**Task:** Given a number n, find a number in the range from 1 to n such that its digit sum is maximum. If there are multiple such numbers, return the largest of them.

#### Examples

##### Example 1

- **Input:**
```text
n = 48
```
- **Output:**
```text
48
```
- **Explanation:** There are two numbers with maximum digit sum = 12. The numbers are 48 and 39. Since 48 > 39, so 48 is the answer.

##### Example 2

- **Input:**
```text
n = 90
```
- **Output:**
```text
89Explanation: 89 gives us the largest digit sum in the range from 1 to n. Hence the answer is 89.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(m) where m is the number of digits in nAuxiliary Space: O(m) where m is the number of digits in n
- **Expected Auxiliary Space Complexity:** O(m) where m is the number of digits in n

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-09 07:19:24
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def findMax(self, n):
        s = str(n)
        answer = n
        max_sum = sum(map(int, s))

        for i in range(len(s)):
            prefix = int(s[:i+1]) - 1
            candidate = int(str(prefix) + '9' * (len(s) - i - 1))

            digit_sum = sum(map(int, str(candidate)))

            if digit_sum > max_sum or (digit_sum == max_sum and candidate > answer):
                max_sum = digit_sum
                answer = candidate

        return answer
```

*Generated on: 9/9/2026, 7:22:55 AM*