# Ex30 Finding Total Cost of Spanning Tree
## DATE:
## AIM:
To write a C Program to implement Prim's Algorithm for finding Total Cost of spanning tree.
## Algorithm
1.Start with any vertex and mark it as visited.
2.Find the minimum weight edge connecting a visited vertex to an unvisited vertex.
3.Include this edge in the spanning tree.
4.Mark the new vertex as visited.  

## Program:
```
/*
Program to implement Prim's Algorithm for finding Total Cost of spanning tree
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/

#include <stdio.h>

#define MAX 10
#define INF 999

int main()
{
    int cost[MAX][MAX], visited[MAX];
    int n, i, j, min, a = 0, b = 0;
    int totalCost = 0, edge_count = 0;

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

    for(i = 0; i < n; i++)
        visited[i] = 0;

    visited[0] = 1; // start from vertex 0

    printf("Edges in Minimum Spanning Tree:\n");

    while(edge_count < n - 1)
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
                        a = i;
                        b = j;
                    }
                }
            }
        }

        printf("Edge (%d, %d) = %d\n", a, b, min);

        totalCost += min;
        visited[b] = 1;
        edge_count++;
    }

    printf("Total cost of spanning tree = %d\n", totalCost);

    return 0;
}
```

## Output:
<img width="456" height="518" alt="image" src="https://github.com/user-attachments/assets/71a0a412-75b3-48ee-82db-ecd644475b44" />



## Result:
Thus the C program to implement Prim's Algorithm for finding Total Cost of spanning tree is implemented successfully.
