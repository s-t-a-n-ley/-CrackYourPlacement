Given a sorted array and a value x, the ceiling of x is the smallest element in an array greater than or equal to x, and the floor is the greatest element smaller than or equal to x. Assume that the array is sorted in non-decreasing order. Write efficient functions to find the floor and ceiling of x. 
Examples : 

For example, let the input array be {1, 2, 8, 10, 10, 12, 19}
For x = 0:    floor doesn't exist in array,  ceil  = 1
For x = 1:    floor  = 1,  ceil  = 1
For x = 5:    floor  = 2,  ceil  = 8
For x = 20:   floor  = 19,  ceil doesn't exist in array

**Solution**
```
def findFloorAndCeil(arr, x):
    left, right = 0, len(arr) - 1
    floor, ceil = None, None
    
    while left <= right:
        mid = left + (right - left) // 2
        
        if arr[mid] == x:
            return arr[mid], arr[mid]
        elif arr[mid] < x:
            floor = arr[mid]
            left = mid + 1
        else:
            ceil = arr[mid]
            right = mid - 1
    
    return floor, ceil

# Example usage
arr = [1, 2, 8, 10, 10, 12, 19]

x = 0
floor, ceil = findFloorAndCeil(arr, x)
print(f"For x = {x}: floor = {floor}, ceil = {ceil}")

x = 1
floor, ceil = findFloorAndCeil(arr, x)
print(f"For x = {x}: floor = {floor}, ceil = {ceil}")

x = 5
floor, ceil = findFloorAndCeil(arr, x)
print(f"For x = {x}: floor = {floor}, ceil = {ceil}")

x = 20
floor, ceil = findFloorAndCeil(arr, x)
print(f"For x = {x}: floor = {floor}, ceil = {ceil}")

```
