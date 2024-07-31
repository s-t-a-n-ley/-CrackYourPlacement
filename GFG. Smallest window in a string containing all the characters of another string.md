Given two strings S and P. Find the smallest window in the string S consisting of all the characters(including duplicates) of the string P.  Return "-1" in case there is no such window present. In case there are multiple such windows of same length, return the one with the least starting index.
Note : All characters are in Lowercase alphabets. 

Example 1:

Input:
S = "timetopractice"
P = "toc"
Output: 
toprac
Explanation: "toprac" is the smallest
substring in which "toc" can be found.

**Solution**
```
def smallest_window(s, p):
    from collections import Counter
    
    if not s or not p or len(s) < len(p):
        return "-1"
    
    # Count characters in P
    required_chars = Counter(p)
    window_chars = Counter()
    
    # Initialize pointers and variables
    l = 0
    min_len = float('inf')
    min_start = 0
    have, need = 0, len(required_chars)
    
    # Expand the window
    for r in range(len(s)):
        char = s[r]
        window_chars[char] += 1
        
        if char in required_chars and window_chars[char] == required_chars[char]:
            have += 1
        
        # Contract the window from the left
        while have == need:
            # Update the minimum window
            if (r - l + 1) < min_len:
                min_len = r - l + 1
                min_start = l
            
            # Remove the leftmost character
            window_chars[s[l]] -= 1
            if s[l] in required_chars and window_chars[s[l]] < required_chars[s[l]]:
                have -= 1
            l += 1
    
    # Return the smallest window or "-1" if no valid window is found
    return s[min_start:min_start + min_len] if min_len != float('inf') else "-1"


```
