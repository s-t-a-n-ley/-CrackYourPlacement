Given an array arr[] of length n. Find all possible unique permutations of the array in sorted order. A sequence A is greater than sequence B if there is an index i for which Aj = Bj for all j<i and Ai > Bi.

Example 1:

Input: 
n = 3
arr[] = {1, 2, 1}
Output: 
1 1 2
1 2 1
2 1 1
Explanation:
These are the only possible unique permutations
for the given array.

**Solution**
```
def permute_unique_sorted(arr):
    def backtrack(start):
        if start == len(arr):
            result.append(arr[:])
            return
        
        seen = set()
        for i in range(start, len(arr)):
            if arr[i] not in seen:
                seen.add(arr[i])
                arr[start], arr[i] = arr[i], arr[start]
                backtrack(start + 1)
                arr[start], arr[i] = arr[i], arr[start]
    
    arr.sort()  # Sort the array to ensure permutations are generated in order
    result = []
    backtrack(0)
    return result

# Example usage
arr = [1, 1, 2]
unique_permutations = permute_unique_sorted(arr)
for perm in unique_permutations:
    print(perm)

```
