## 01. Range GCD Queries

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/range-gcd-queries3654/1)

### Problem Description

**Task:** Given an integer array arr[] and a 2D array queries[][] containing q queries, where each query is one of the following two types:Type 1: [0, l, r] - > Return the GCD of all elements in the range [l, r] (both inclusive).Type 2: [1, index, value] - > Update arr[index] to value.Return an array containing the answers to all Type 1 queries in the order they appear in queries[][].Note: Use 0-based indexing.Examples:Input: arr[] = [2, 3, 4, 6, 8, 16], q = 3, queries[][] = [[0, 0, 2], [1, 3, 8], [0, 2, 5]]

#### Examples

##### Example 1

- **Output:**
```text
[1, 4]
```
- **Explanation:** Initially, arr[] = [2, 3, 4, 6, 8, 16]. Query [0, 0, 2]: Find the GCD of the subarray arr[0...2] = [2, 3, 4]. The GCD is 1. Query [1, 3, 8]: Update arr[3] from 6 to 8. The array becomes [2, 3, 4, 8, 8, 16]. Query [0, 2, 5]: Find the GCD of the subarray arr[2...5] = [4, 8, 8, 16]. The GCD is 4. Therefore, the answers to all Type 0 queries are [1, 4].

##### Example 2

- **Input:**
```text
arr[] = [12, 18, 24, 30, 36], q = 4, queries[][] = [[0, 1, 3], [1, 2, 15], [0, 0, 2], [0, 2, 4]]Output: [6, 3, 3]Explanation: Initially, arr[] = [12, 18, 24, 30, 36].Query [0, 1, 3]: Find the GCD of the subarray arr[1...3] = [18, 24, 30]. The GCD is 6.Query [1, 2, 15]: Update arr[2] from 24 to 15. The array becomes [12, 18, 15, 30, 36].Query [0, 0, 2]: Find the GCD of the subarray arr[0...2] = [12, 18, 15]. The GCD is 3.Query [0, 2, 4]: Find the GCD of the subarray arr[2...4] = [15, 30, 36]. The GCD is 3.Therefore, the answers to all Type 0 queries are [6, 3, 3].Constraints:1 ≤ arr.size() ≤ 10⁵¹ ≤ q ≤ 10⁵⁰ ≤ l, r, index ≤ arr.size()-11 ≤ arr[i], value ≤ 10⁵
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O((arr.size()+q)*log n*log(max_element(arr)))
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Python)

- **Submitted:** 2026-09-28 06:55:41
- **Status:** Correct
- **Marks:** 4

```python
from math import gcd

class Solution:
    def processQueries(self, arr, queries):
        n = len(arr)
        size = 1

        while size < n:
            size *= 2

        tree = [0] * (2 * size)

        for i in range(n):
            tree[size + i] = arr[i]

        for i in range(size - 1, 0, -1):
            tree[i] = gcd(tree[2 * i], tree[2 * i + 1])

        def update(index, value):
            pos = size + index
            tree[pos] = value
            pos //= 2

            while pos:
                tree[pos] = gcd(tree[2 * pos], tree[2 * pos + 1])
                pos //= 2

        def query(left, right):
            left += size
            right += size
            result = 0

            while left <= right:
                if left % 2 == 1:
                    result = gcd(result, tree[left])
                    left += 1

                if right % 2 == 0:
                    result = gcd(result, tree[right])
                    right -= 1

                left //= 2
                right //= 2

            return result

        ans = []

        for q in queries:
            if q[0] == 1:
                update(q[1], q[2])
            else:
                ans.append(query(q[1], q[2]))

        return ans
```

*Generated on: 9/28/2026, 6:56:14 AM*