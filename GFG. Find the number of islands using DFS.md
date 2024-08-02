Code
```
def numIslands(grid):
    if not grid:
        return 0
    
    rows, cols = len(grid), len(grid[0])
    count = 0
    
    def dfs(r, c):
        if r < 0 or r >= rows or c < 0 or c >= cols or grid[r][c] == '0':
            return
        grid[r][c] = '0'  # Mark the land cell as visited by sinking the island
        # Explore all 8 possible directions
        directions = [
            (1, 0), (-1, 0), (0, 1), (0, -1),   # up, down, left, right
            (1, 1), (1, -1), (-1, 1), (-1, -1)  # diagonals
        ]
        for dr, dc in directions:
            dfs(r + dr, c + dc)
    
    for r in range(rows):
        for c in range(cols):
            if grid[r][c] == '1':
                count += 1  # Found an island
                dfs(r, c)  # Sink the island
    
    return count

# Example usage:
grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]

print(numIslands(grid))  # Output: 1

```
