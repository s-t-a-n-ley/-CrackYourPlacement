You are given an array arr[] of N integers. The task is to find the smallest positive number missing from the array.

Note: Positive number starts from 1.

**Solution**
```
def find_smallest_missing_positive(arr):
    n = len(arr)
    
    # Step 1: Mark elements which are out of range or non-positive
    for i in range(n):
        if arr[i] <= 0 or arr[i] > n:
            arr[i] = n + 1
    
    # Step 2: Use indices to mark the presence of elements
    for i in range(n):
        num = abs(arr[i])
        if num <= n:
            arr[num - 1] = -abs(arr[num - 1])
    
    # Step 3: Find the first positive index
    for i in range(n):
        if arr[i] > 0:
            return i + 1
    
    return n + 1

# Example usage:
arr = [3, 4, -1, 1]
print("The smallest positive missing number is:", find_smallest_missing_positive(arr))

```
