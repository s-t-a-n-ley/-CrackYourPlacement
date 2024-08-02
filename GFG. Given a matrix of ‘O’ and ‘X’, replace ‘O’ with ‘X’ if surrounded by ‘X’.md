Given a matrix where every element is either ‘O’ or ‘X’, replace ‘O’ with ‘X’ if surrounded by ‘X’. A ‘O’ (or a set of ‘O’) is considered to be surrounded by ‘X’ if there are ‘X’ at locations just below, just above, just left, and just right of it. 

**Solution**
```
def solve(board):
    if not board:
        return
    
    rows, cols = len(board), len(board[0])
    
    def dfs(r, c):
        if r < 0 or r >= rows or c < 0 or c >= cols or board[r][c] != 'O':
            return
        board[r][c] = 'E'  # Temporarily mark the 'O' as 'E'
        directions = [(1, 0), (-1, 0), (0, 1), (0, -1)]  # up, down, left, right
        for dr, dc in directions:
            dfs(r + dr, c + dc)
    
    # Step 1: Mark the 'O's on the border and connected to border 'O's
    for r in range(rows):
        if board[r][0] == 'O':
            dfs(r, 0)
        if board[r][cols - 1] == 'O':
            dfs(r, cols - 1)
    for c in range(cols):
        if board[0][c] == 'O':
            dfs(0, c)
        if board[rows - 1][c] == 'O':
            dfs(rows - 1, c)
    
    # Step 2: Convert the remaining 'O's to 'X's
    for r in range(rows):
        for c in range(cols):
            if board[r][c] == 'O':
                board[r][c] = 'X'
    
    # Step 3: Convert the marked 'E's back to 'O's
    for r in range(rows):
        for c in range(cols):
            if board[r][c] == 'E':
                board[r][c] = 'O'

# Example usage:
board = [
  ['X', 'X', 'X', 'X'],
  ['X', 'O', 'O', 'X'],
  ['X', 'X', 'O', 'X'],
  ['X', 'O', 'X', 'X']
]

solve(board)

for row in board:
    print(row)

```
