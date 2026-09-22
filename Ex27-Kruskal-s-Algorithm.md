# Ex27 Kruskal’s Algorithm
## DATE:
## AIM:
To write a C program to implement Kruskal's Algorithm for finding minimum cost

## Algorithm
1.Start with a graph having n vertices and e edges.
2.Sort all the edges in increasing order of their weights.
3.Initialize parent array for all vertices (for cycle detection).
4.Select the smallest edge and check if it forms a cycle.
5.If it does not form a cycle, include it in the Minimum Spanning Tree (MST).
6.Repeat until (n-1) edges are selected.

## Program:
```
/*
Program to implement Kruskal's Algorithm
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/

#include <stdio.h>

#define MAX 10

int parent[MAX];

int find(int i)
{
    while(parent[i])
        i = parent[i];
    return i;
}

int union_set(int i, int j)
{
    if(i != j)
    {
        parent[j] = i;
        return 1;
    }
    return 0;
}

int main()
{
    int n, cost[MAX][MAX];
    int i, j, a, b, u, v;
    int min, mincost = 0, edge_count = 0;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix:\n");
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);
            if(cost[i][j] == 0)
                cost[i][j] = 999; // No edge
        }
    }

    for(i = 0; i < n; i++)
        parent[i] = 0;

    printf("Edges of Minimum Spanning Tree:\n");

    while(edge_count < n - 1)
    {
        min = 999;

        for(i = 0; i < n; i++)
        {
            for(j = 0; j < n; j++)
            {
                if(cost[i][j] < min)
                {
                    min = cost[i][j];
                    a = u = i;
                    b = v = j;
                }
            }
        }

        u = find(u);
        v = find(v);

        if(union_set(u, v))
        {
            printf("%d edge (%d,%d) = %d\n", edge_count + 1, a, b, min);
            mincost += min;
            edge_count++;
        }

        cost[a][b] = cost[b][a] = 999;
    }

    printf("Minimum cost = %d\n", mincost);

    return 0;
}
```

## Output:


<img width="475" height="505" alt="image" src="https://github.com/user-attachments/assets/13bec0bb-892a-49ab-9a0e-06b42c8a708a" />

## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.
