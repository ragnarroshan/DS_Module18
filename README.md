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




# Ex29 Travelling Salesman Problem
## DATE:
## AIM:
To write a C Program to implement Travelling Salesman Problem for finding shortest path.
## Algorithm
1. Start from a selected source city.
2.Mark the current city as visited.
3.Find the nearest unvisited city.
4.Repeat until all cities are visited.
5.Return to the starting city and calculate total cost.
## Program:
```
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/

#include <stdio.h>

#define MAX 10
#define INF 999

int n, cost[MAX][MAX], visited[MAX];

void tsp(int city)
{
    int i, nextCity = -1;
    int min = INF;

    visited[city] = 1;
    printf("%d -> ", city);

    for(i = 0; i < n; i++)
    {
        if(cost[city][i] != 0 && !visited[i])
        {
            if(cost[city][i] < min)
            {
                min = cost[city][i];
                nextCity = i;
            }
        }
    }

    if(nextCity == -1)
    {
        printf("0");
        return;
    }

    tsp(nextCity);
}

int calculateCost()
{
    int i, j;
    int total = 0;
    int current = 0;

    for(i = 0; i < n; i++)
        visited[i] = 0;

    for(i = 0; i < n - 1; i++)
    {
        visited[current] = 1;
        int min = INF, next = -1;

        for(j = 0; j < n; j++)
        {
            if(cost[current][j] && !visited[j])
            {
                if(cost[current][j] < min)
                {
                    min = cost[current][j];
                    next = j;
                }
            }
        }

        total += min;
        current = next;
    }

    total += cost[current][0]; // return to start
    return total;
}

int main()
{
    int i, j;

    printf("Enter number of cities: ");
    scanf("%d", &n);

    printf("Enter cost matrix:\n");
    for(i = 0; i < n; i++)
    {
        for(j = 0; j < n; j++)
        {
            scanf("%d", &cost[i][j]);
        }
    }

    printf("Path: ");
    tsp(0);

    int minCost = calculateCost();
    printf("\nMinimum Cost: %d\n", minCost);

    return 0;
}
```

## Output:


<img width="585" height="582" alt="image" src="https://github.com/user-attachments/assets/e8be9fc9-b42e-4fef-acff-bd1145208a4a" />

## Result:
Thus, the C program to implement Travelling Salesman Problem for finding shortest path is implemented successfully.




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
