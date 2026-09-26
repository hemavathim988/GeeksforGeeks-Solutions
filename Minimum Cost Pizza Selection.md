## 01. Minimum Cost Pizza Selection

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pizza-mania0155/1)

### Problem Description

**Task:** Given the area of Small, Medium, and Large pizzas as s, m, and l units, and their respective costs as cs, cm, and cl, find the minimum amount of money required to buy pizzas whose total area is at least x. You may buy any number of pizzas of each type.

#### Examples

##### Example 1

- **Input:**
```text
x = 16, s = 3, m = 6, l = 9, cs = 50, cm = 150, cl = 300
```
- **Output:**
```text
300
```
- **Explanation:** We want at least 16 sq. units of Pizza. One unit of each s, m and l = 3 + 6 + 9 = 18 sq units, Cost = 500. 6 units of s = 18 sq units, Cost = 300 2 units of l = 18 sq units, Cost = 600 etc. Of all the Arrangements, Minimum Cost is Rs. 300.

##### Example 2

- **Input:**
```text
x = 10, s = 1, m = 3, l = 10, cs = 10, cm = 20, cl = 50
```
- **Output:**
```text
50
```
- **Explanation:** Of all the Arrangements possible, Minimum Cost is Rs. 50.

#### Constraints

- **1.** `1 ≤ x ≤ 5001 ≤ s ≤ m ≤ l ≤ 1001 ≤ cs ≤ cm ≤ cl ≤ 100`

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(x)
- **Expected Auxiliary Space Complexity:** O(x)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-26 07:35:55
- **Status:** Correct
- **Marks:** 4

```python
class Solution:
    def minimumCost(self, x, s, m, l, cs, cm, cl):
        ans = float('inf')

        for i in range(x // s + 2):
            for j in range(x // m + 2):
                area = i * s + j * m

                if area >= x:
                    ans = min(ans, i * cs + j * cm)

                if area < x:
                    remaining = x - area
                    k = (remaining + l - 1) // l
                    ans = min(ans, i * cs + j * cm + k * cl)

        return ans
```

*Generated on: 9/26/2026, 7:36:26 AM*