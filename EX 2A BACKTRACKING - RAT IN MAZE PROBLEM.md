# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1. Initialize a solution matrix sol of the same size as the maze, filled with zeros.
2. Start from cell (0, 0) and attempt to reach the destination cell (N-1, N-1).
3. Check if the current cell is safe (i.e., within bounds and not blocked). If safe, mark it as part of the path.
4. Recursively move either right or down, trying to find a path to the goal. If neither move works, backtrack by unmarking the current cell.
5. If a path is found, print the solution matrix; otherwise, print that no solution exists.  
## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: Praveen V
Register Number:  212222040121
*/
```
```python
def is_path(n, maze, r, c):
    if r < 0 or c < 0 or r >= n or c >= n or maze[r][c] == 0 or sol[r][c] == 1:
        return False
    if r == n - 1 and c == n - 1:
        sol[r][c] = 1
        return True
    
    sol[r][c] = 1

    # Move Right
    if is_path(n, maze, r, c + 1):
        return True
    # Move Down
    if is_path(n, maze, r + 1, c):
        return True
    # Move Left
    if is_path(n, maze, r, c - 1):
        return True
    # Move Up
    if is_path(n, maze, r - 1, c):
        return True

    sol[r][c] = 0  # Backtrack
    return False

n = 4
maze = [[1, 0, 0, 0],
        [1, 1, 0, 0],
        [0, 1, 0, 0],
        [0, 1, 1, 1]]

sol = [[0 for j in range(n)] for i in range(n)]

if is_path(n, maze, 0, 0):
    for i in range(n):
        for j in range(n):
            print(sol[i][j], end=' ')
        print()
else:
    print("No path is available")

```
## Output:
![Screenshot 2025-04-26 110148](https://github.com/user-attachments/assets/047c22b5-2ec1-45e1-b1a5-0ff9e5364f93)
## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
