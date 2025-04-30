# EX 2B BACKTRACKING - NQUEEN PROBLEM
## DATE:
## AIM:
To solve the N-Queen problem using backtracking, which places N queens on an N*N chessboard such that no two queens threaten each other.


## Algorithm
1. Read the value of N and create an N x N chessboard initialized with 0s.
2. Define a function isSafe() to check if a queen can be placed at a given position by ensuring no other queens threaten it horizontally, and diagonally (upper-left and lower-left).
3. Use a recursive function solveNQUtil() that tries to place queens column by column.
4. If a safe position is found, place the queen and recursively try to place the rest; if it fails, backtrack and remove the queen.
5. Print the board if a solution is found; otherwise, print "Solution does not exist".   
## Program:
```
/*
Program to implement N-Queen problem using backtracking.
Developed by: ArunKumar.T
Register Number:  212222040017
*/
```
```python
def is_safe(board, row, col, n):
    for c in range(col, -1, -1):
        if board[row][c] == 1:
            return False

    i = row
    j = col
    while i >= 0 and j >= 0:
        if board[i][j] == 1:
            return False
        i -= 1
        j -= 1

    i = row
    j = col
    
    while i < n and j >= 0:
        if board[i][j] == 1:
            return False
        i += 1
        j -= 1

    return True
    
def nQueens(board, col, n):
    if col >= n:
        return True

    for i in range(n):
        if is_safe(board, i, col, n):
            board[i][col] = 1
            if nQueens(board, col + 1, n):
                return True
            board[i][col] = 0

    return False

n = int(input())

board = [[0 for j in range(n)] for i in range(n)]

if nQueens(board, 0, n):
    for i in range(n):
        for j in range(n):
            print(board[i][j], end=' ')
        print()
else:
    print("Solution does not exist")
    
```
## Output:
![Screenshot 2025-04-26 110319](https://github.com/user-attachments/assets/e99280b5-30fe-4c6d-a480-59f5d68983b6)
## Result:
The N-Queens program executed successfully, and a valid board configuration was generated.
