# EX 2A BACKTRACKING - RAT IN MAZE PROBLEM
## DATE:
## AIM:
To implement the Rat in a Maze problem using backtracking and find all possible paths from the start to the destination in a given maze.


## Algorithm
1.Start at (0,0) in the maze and mark the cell as part of the path.
2.Check if the current cell is the destination (N-1, N-1); if yes, the path is complete.
3.Move Forward: Try moving down (x+1, y) and right (x, y+1) recursively.
4.Backtrack: If neither move leads to a solution, mark the cell as 0 (unvisited) and backtrack.
5.Repeat until all valid paths are explored or one valid path is found.

## Program:
```
/*
Program to implement Rat in a Maze.
Developed by: SUROTHAAMAN R
Register Number:  212222103003
*/
```
```
N = 4
 
def printSolution( sol ):
     
    for i in sol:
        for j in i:
            print(str(j) + " ", end ="")
        print("")
 

def isSafe( maze, x, y ):
     
    if x >= 0 and x < N and y >= 0 and y < N and maze[x][y] == 1:
        return True
     
    return False
 

def solveMaze( maze ):
     
    # Creating a 4 * 4 2-D list
    sol = [ [ 0 for j in range(4) ] for i in range(4) ]
     
    if solveMazeUtil(maze, 0, 0, sol) == False:
        print("Solution doesn't exist");
        return False
     
    printSolution(sol)
    return True
     

def solveMazeUtil(maze, x, y, sol):
#Write your code here     
    if x == N - 1 and y == N - 1:
        sol[x][y] = 1
        return True
    if isSafe(maze, x, y) == True:
        sol[x][y] = 1
        if solveMazeUtil(maze, x + 1, y, sol) == True:
            return True
        if solveMazeUtil(maze, x, y + 1, sol) == True:
            return True
        sol[x][y] = 0
        return False
        
if __name__ == "__main__":
    # Initialising the maze
    maze = [ [1, 0, 0, 0],
             [1, 1, 0, 1],
             [0, 1, 0, 0],
             [1, 1, 1, 1] ]
              
    solveMaze(maze)
```
## Output:

![image](https://github.com/user-attachments/assets/bb6b387d-9680-4bd7-a5f2-891922dde3a4)


## Result:
The Rat in a Maze program executed successfully, and a valid path from the start to the destination was found and display.
