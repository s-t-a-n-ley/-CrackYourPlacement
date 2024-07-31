Given an array nums[] of size n, where nums[i] denotes the number of characters in one word. Let K be the limit on the number of characters that can be put in one line (line width). Put line breaks in the given sequence such that the lines are printed neatly.
Assume that the length of each word is smaller than the line width. When line breaks are inserted there is a possibility that extra spaces are present in each line. The extra spaces include spaces put at the end of every line except the last one. 

You have to minimize the following total cost where total cost = Sum of cost of all lines, where cost of line is = (Number of extra spaces in the line)2.

**Solution**
```
def solveWordWrap(nums, K):
    n = len(nums)
    
    # Initialize dp and breaks array
    dp = [float('inf')] * (n + 1)
    breaks = [-1] * (n + 1)
    
    # dp[0] is 0 because no words means no cost
    dp[0] = 0
    
    # Calculate the cost of each possible line
    for i in range(1, n + 1):
        line_length = 0
        for j in range(i, 0, -1):
            line_length += nums[j - 1]
            if line_length > K:
                break
            if j < i:
                line_length += 1  # add space between words
            extra_spaces = K - line_length
            cost = dp[j - 1] + extra_spaces ** 2
            if cost < dp[i]:
                dp[i] = cost
                breaks[i] = j - 1

    # Reconstruct the solution
    lines = []
    end = n
    while end > 0:
        start = breaks[end]
        lines.append((start + 1, end))
        end = start
    
    lines.reverse()
    return dp[n], lines


```
