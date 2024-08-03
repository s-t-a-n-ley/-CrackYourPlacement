Given two arrays of equal size n and an integer k. The task is to permute both arrays such that sum of their corresponding element is greater than or equal to k i.e a[i] + b[i] >= k. The task is to print “Yes” if any such permutation exists, otherwise print “No”.

Examples : 

Input : a[] = {2, 1, 3}, 
        b[] = { 7, 8, 9 }, 
        k = 10. 
Output : Yes
Permutation  a[] = { 1, 2, 3 } and b[] = { 9, 8, 7 } 
satisfied the condition a[i] + b[i] >= K.

Input : a[] = {1, 2, 2, 1}, 
        b[] = { 3, 3, 3, 4 }, 
        k = 5. 
Output : No

**Solution**
```
def can_permute_arrays(a, b, k):
    # Sort array a in ascending order
    a.sort()
    
    # Sort array b in descending order
    b.sort(reverse=True)
    
    # Check if each pair satisfies the condition
    for i in range(len(a)):
        if a[i] + b[i] < k:
            return "No"
    
    return "Yes"
```
