Given an array of strings, return all groups of strings that are anagrams. The groups must be created in order of their appearance in the original array. Look at the sample case for clarification.

Note: The final output will be in lexicographic order.

**Solution**
```
from collections import defaultdict

def group_anagrams(strs):
    anagrams = defaultdict(list)
    
    # Step 1: Group strings by sorted characters
    for s in strs:
        sorted_s = ''.join(sorted(s))
        anagrams[sorted_s].append(s)
    
    # Step 2: Sort each group lexicographically
    for key in anagrams:
        anagrams[key].sort()
    
    # Step 3: Collect groups in order of appearance
    result = [anagrams[key] for key in anagrams]
    
    # Step 4: Sort the final list of groups lexicographically
    result.sort()
    
    return result

# Example usage:
strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
print(group_anagrams(strs))

```
