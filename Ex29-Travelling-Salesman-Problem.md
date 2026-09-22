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
