Given an array arr[] of size n and an integer x, return 1 if there exists a pair of elements in the array whose absolute difference is x, otherwise, return -1.

Example 1:

Input:
n = 6
x = 78
arr[] = {5, 20, 3, 2, 5, 80}
Output:
1
Explanation:
Pair (2, 80) have absolute difference of 78.

**Solution**
```
def findPairWithDifference(arr, n, x):
    # Create a hash set to store array elements
    elements = set()
    
    # Iterate through each element in the array
    for num in arr:
        # Check if either num + x or num - x exists in the set
        if (num + x) in elements or (num - x) in elements:
            return 1
        # Add the current element to the set
        elements.add(num)
    
    # If no such pair is found, return -1
    return -1

# Example usage
arr1 = [5, 20, 3, 2, 5, 80]
n1 = len(arr1)
x1 = 78
print(findPairWithDifference(arr1, n1, x1))  # Output: 1

arr2 = [1, 2, 3, 4, 5]
n2 = len(arr2)
x2 = 10
print(findPairWithDifference(arr2, n2, x2))  # Output: -1

```
