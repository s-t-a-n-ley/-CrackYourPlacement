Given an array of n distinct integers. The task is to check whether reversing any one sub-array can make the array sorted or not. If the array is already sorted or can be made sorted by reversing any one subarray, print “Yes“, else print “No“.

Examples: 

Input : arr [] = {1, 2, 5, 4, 3}
Output : Yes
By reversing the subarray {5, 4, 3}, the array will be sorted.

Input : arr [] = { 1, 2, 4, 5, 3 }
Output : No

**Solution**
```
def can_sort_by_reversing_subarray(arr):
    n = len(arr)
    
    # Step 1: Find the first decreasing point
    l = 0
    while l < n - 1 and arr[l] <= arr[l + 1]:
        l += 1
    
    # If the whole array is sorted already
    if l == n - 1:
        return "Yes"
    
    # Step 2: Find the first increasing point from the end
    r = n - 1
    while r > 0 and arr[r] >= arr[r - 1]:
        r -= 1
    
    # Step 3: Reverse the subarray from l to r
    arr[l:r+1] = arr[l:r+1][::-1]
    
    # Check if the array is sorted after reversing
    if all(arr[i] <= arr[i + 1] for i in range(n - 1)):
        return "Yes"
    else:
        return "No"

# Examples
arr1 = [1, 2, 5, 4, 3]
arr2 = [1, 2, 4, 5, 3]

print(can_sort_by_reversing_subarray(arr1))  # Output: Yes
print(can_sort_by_reversing_subarray(arr2))  # Output: No

```
