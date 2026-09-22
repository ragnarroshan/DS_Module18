# Ex26 Prim’s Algorithm
## DATE:
## AIM:
To write a C program to implement Prim's Algorithm for finding Total Cost of tree.

## Algorithm
1.Start the program
2.Input number of vertices and cost adjacency matrix
3.Select a starting vertex and mark it as visited
4.Find the minimum cost edge connecting visited and unvisited vertices
5.Add the selected edge to the spanning tree and mark the vertex as visited
6.Repeat until all vertices are included
7.Calculate total cost of the spanning tree
8.Display edges and total cost
9.Stop   

## Program:
```
/*
Program to implement Prim's Algorithm
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/

#include<stdio.h>

#define MAX 10
#define INF 999

int main()
{
    int cost[MAX][MAX], visited[MAX] = {0};
    int n, i, j, ne = 1;
    int min, a = 0, b = 0, u = 0, v = 0;
    int totalCost = 0;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter cost adjacency matrix:\n");
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);
            if(cost[i][j] == 0)
                cost[i][j] = INF;
        }
    }

    visited[0] = 1; // start from vertex 0

    printf("\nEdges in MST:\n");

    while(ne < n)
    {
        min = INF;

        for(i = 0; i < n; i++)
        {
            if(visited[i])
            {
                for(j = 0; j < n; j++)
                {
                    if(!visited[j] && cost[i][j] < min)
                    {
                        min = cost[i][j];
                        a = u = i;
                        b = v = j;
                    }
                }
            }
        }

        printf("%d -> %d = %d\n", a, b, min);

        totalCost += min;
        visited[b] = 1;
        ne++;
    }

    printf("\nTotal cost of MST = %d\n", totalCost);

    return 0;
}
```

## Output:
<img width="437" height="485" alt="image" src="https://github.com/user-attachments/assets/6fb54053-6d8e-4563-b71f-b9236e221401" />




## Result:
Thus, the C program to implement Prim's Algorithm for finding Total Cost of tree is implemented successfully.
