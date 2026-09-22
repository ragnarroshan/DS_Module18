# Ex28 Dijkstra’s Algorithm
## DATE:
## AIM:
To write a C Program to implement Dijkstra's Algorithm to find the shortest path

## Algorithm
1.Initialize all distances as infinity except the source vertex (set to 0).
2.Mark all vertices as unvisited.
3.Select the vertex with the minimum distance (unvisited).
4.Update the distance of its adjacent vertices.
5.Repeat until all vertices are visited.  

## Program:
```
/*
Program to implement Dijkstra's Algorithm 
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/

#include <stdio.h>

#define MAX 10
#define INF 999

int main()
{
    int cost[MAX][MAX], dist[MAX], visited[MAX];
    int n, i, j, count, min, u, source;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter the cost adjacency matrix:\n");
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);
            if(cost[i][j] == 0 && i != j)
                cost[i][j] = INF;
        }
    }

    printf("Enter the source vertex: ");
    scanf("%d", &source);

    for(i = 0; i < n; i++)
    {
        dist[i] = cost[source][i];
        visited[i] = 0;
    }

    dist[source] = 0;
    visited[source] = 1;

    count = 1;

    while(count < n)
    {
        min = INF;

        for(i = 0; i < n; i++)
        {
            if(dist[i] < min && !visited[i])
            {
                min = dist[i];
                u = i;
            }
        }

        visited[u] = 1;

        for(i = 0; i < n; i++)
        {
            if(!visited[i] && (min + cost[u][i] < dist[i]))
            {
                dist[i] = min + cost[u][i];
            }
        }

        count++;
    }

    printf("Shortest distances from vertex %d:\n", source);
    for(i = 0; i < n; i++)
    {
        printf("To %d = %d\n", i, dist[i]);
    }

    return 0;
}
```

## Output:

<img width="554" height="601" alt="image" src="https://github.com/user-attachments/assets/3c51b78b-05a6-4a7a-84da-60569c9e6a1c" />


## Result:
Thus, the Program to implement Dijkstra's Algorithm to find the shortest path is implemented successfully.
