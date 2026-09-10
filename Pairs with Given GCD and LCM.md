## 01. Pairs with Given GCD and LCM

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/possible-pairs1550/1)

### Problem Description

**Task:** Given two integers x and y representing the GCD and LCM of two unknown positive integers a and b, count the number of valid pairs (a, b) satisfying these conditions. Note that (a, b) and (b, a) are counted as distinct pairs when a ≠ b.

#### Examples

##### Example 1

- **Input:**
```text
x = 2, y = 12
```
- **Output:**
```text
4
```
- **Explanation:** The valid pairs are (2, 12), (4, 6), (6, 4), and (12, 2), since each pair has GCD = 2 and LCM = 12.

##### Example 2

- **Input:**
```text
x = 6, y = 4
```
- **Output:**
```text
0
```
- **Explanation:** LCM must always be a multiple of GCD. Since y is not divisible by x, no valid pair exists.

#### Constraints

- **1.** `1 ≤ x, y ≤ 10⁴`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(sqrt(n)log(n))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-10 07:14:40
- **Status:** Correct
- **Marks:** 2

```python
class Solution:
    def pairCount(self, x, y):
        if y % x != 0:
            return 0

        n = y // x
        count = 0

        p = 2
        while p * p <= n:
            if n % p == 0:
                count += 1

                while n % p == 0:
                    n //= p

            p += 1

        if n > 1:
            count += 1

        return 2 ** count
```

*Generated on: 9/10/2026, 7:15:17 AM*