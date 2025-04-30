## EX 2D BACKTRACKING - GRAPH COLORING PROBLEM
## DATE:
## AIM:
To solve the Graph Coloring Problem using backtracking, assigning colors to the vertices of a graph such that no two adjacent vertices share the same color while minimizing the number of colors used.



## Algorithm
1. Create a graph using an adjacency matrix for V vertices.
2. Initialize a color array with 0 (unassigned) for all vertices.
3. Use backtracking to assign colors (1 to m) to each vertex.
4. Ensure no two adjacent vertices have the same color using is_safe().
5. Print the color assignment if successful; else, print "Solution does not exist".
## Program:
```
/*
Program to implement Graph Coloring Problem using backtracking.
Developed by: Praveen V
Register Number: 212222040121
*/
```
```python
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [[0] * vertices for _ in range(vertices)]

    def is_safe(self, v, color, c):
        for i in range(self.V):
            if self.graph[v][i] == 1 and color[i] == c:
                return False
        return True

    def graph_coloring_util(self, m, color, v):
        if v == self.V:
            return True

        for c in range(1, m + 1):
            if self.is_safe(v, color, c):
                color[v] = c 
                
                if self.graph_coloring_util(m, color, v + 1):
                    return True
                
                color[v] = 0

        return False

    def graphColouring(self, m):
       
        color = [0] * self.V 

        if not self.graph_coloring_util(m, color, 0):
            print("Solution does not exist")
            return None

        print("Solution exist and Following are the assigned colours:")
        print(" ".join(map(str, color)))
```

## Output:
![Screenshot 2025-04-26 111138](https://github.com/user-attachments/assets/4f71f11d-f92d-4e0a-8de1-f08c74b861b0)
![Screenshot 2025-04-26 111153](https://github.com/user-attachments/assets/653f7091-885b-4aa0-8aeb-85526e2fd5fd)
![Screenshot 2025-04-26 111201](https://github.com/user-attachments/assets/a8607e7d-bd02-44f5-aa6c-b9ae15cd48be)
## Result:
The Graph Coloring program executed successfully, and the colors were assigned to the vertices such that no two adjacent vertices share the same color.
