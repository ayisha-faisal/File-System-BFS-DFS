#include <stdio.h>
#include <string.h>

#define V 5

int graph[V][V] = {
    {0, 1, 1, 0, 0},
    {1, 0, 0, 1, 0},
    {1, 0, 0, 1, 1},
    {0, 1, 1, 0, 1},
    {0, 0, 1, 1, 0}
};

char *files[V] = {
    "Root",
    "Documents",
    "Downloads",
    "notes.txt",
    "photo.jpg"
};

int visited[V];

// BFS Search
void BFS(int start, char target[])
{
    int queue[V];
    int front = 0, rear = 0;
    int found = 0;

    for(int i = 0; i < V; i++)
        visited[i] = 0;

    visited[start] = 1;
    queue[rear++] = start;

    printf("\nBFS Traversal: ");

    while(front < rear)
    {
        int node = queue[front++];

        printf("%s ", files[node]);

        if(strcmp(files[node], target) == 0)
            found = 1;

        for(int i = 0; i < V; i++)
        {
            if(graph[node][i] == 1 && !visited[i])
            {
                visited[i] = 1;
                queue[rear++] = i;
            }
        }
    }

    if(found)
        printf("\nFile found using BFS!\n");
    else
        printf("\nFile not found using BFS!\n");
}

// DFS Search
int DFS(int node, char target[])
{
    int found = 0;

    visited[node] = 1;

    printf("%s ", files[node]);

    if(strcmp(files[node], target) == 0)
        found = 1;

    for(int i = 0; i < V; i++)
    {
        if(graph[node][i] == 1 && !visited[i])
        {
            if(DFS(i, target))
                found = 1;
        }
    }

    return found;
}

int main()
{
    int start;
    char target[30];

    printf("FILE SYSTEM USING GRAPH\n");

    printf("\nAdjacency Matrix:\n");

    for(int i = 0; i < V; i++)
    {
        for(int j = 0; j < V; j++)
            printf("%d ", graph[i][j]);

        printf("\n");
    }

    printf("\nNodes:\n");

    for(int i = 0; i < V; i++)
        printf("%d - %s\n", i, files[i]);

    printf("\nEnter starting node (0-4): ");
    scanf("%d", &start);

    if(start < 0 || start >= V)
    {
        printf("Invalid starting node!\n");
        return 0;
    }

    printf("Enter file name to search: ");
    scanf("%29s", target);

    BFS(start, target);

    for(int i = 0; i < V; i++)
        visited[i] = 0;

    printf("\nDFS Traversal: ");

    int result = DFS(start, target);

    if(result)
        printf("\nFile found using DFS!\n");
    else
        printf("\nFile not found using DFS!\n");

    return 0;
}
