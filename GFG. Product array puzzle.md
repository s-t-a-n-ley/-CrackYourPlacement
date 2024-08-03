Given an array nums[], construct a Product Array P (of same size n) such that P[i] is equal to the product of all the elements of nums except nums[i].

**Solution**
```
from typing import List

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        if n == 0:
            return []

        left_products = [1] * n
        right_products = [1] * n
        result = [1] * n

        # Fill left_products
        for i in range(1, n):
            left_products[i] = left_products[i - 1] * nums[i - 1]

        # Fill right_products
        for i in range(n - 2, -1, -1):
            right_products[i] = right_products[i + 1] * nums[i + 1]

        # Construct the result from left_products and right_products
        for i in range(n):
            result[i] = left_products[i] * right_products[i]

        return result

```
