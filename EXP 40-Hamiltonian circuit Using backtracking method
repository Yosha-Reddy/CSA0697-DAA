#include <stdio.h>
#include <stdbool.h>

#define MAX_VERTICES 10
bool isSafe(int v, int path[], int graph[MAX_VERTICES][MAX_VERTICES], int pathLength, int pos) {
    if (!graph[path[pos - 1]][v]) {
        return false;
    }

    for (int i = 0; i < pathLength; i++) {
        if (path[i] == v) {
            return false;
        }
    }

    return true;
}

bool hamiltonianCycleUtil(int graph[MAX_VERTICES][MAX_VERTICES], int path[], int pathLength, int totalVertices) {
    if (pathLength == totalVertices) {
        if (graph[path[pathLength - 1]][path[0]]) {
            return true;
        }
        return false;
    }

    for (int v = 1; v < totalVertices; v++) {
        if (isSafe(v, path, graph, pathLength, pathLength)) {
            path[pathLength] = v;

            if (hamiltonianCycleUtil(graph, path, pathLength + 1, totalVertices)) {
                return true;
            }

            path[pathLength] = -1; 
        }
    }

    return false;
}

bool hamiltonianCycle(int graph[MAX_VERTICES][MAX_VERTICES], int totalVertices) {
    int path[MAX_VERTICES];
    for (int i = 0; i < totalVertices; i++) {
        path[i] = -1;
    }
    path[0] = 0;

    if (!hamiltonianCycleUtil(graph, path, 1, totalVertices)) {
        printf("No Hamiltonian cycle exists.\n");
        return false;
    }

    printf("Hamiltonian cycle exists:\n");
    for (int i = 0; i < totalVertices; i++) {
        printf("%d ", path[i]);
    }
    printf("%d\n", path[0]);
    return true;
}

int main() {
    int totalVertices;

    printf("Enter the number of vertices in the graph: ");
    scanf("%d", &totalVertices);

    int graph[MAX_VERTICES][MAX_VERTICES];
    printf("Enter the adjacency matrix for the graph:\n");
    for (int i = 0; i < totalVertices; i++) {
        for (int j = 0; j < totalVertices; j++) {
            scanf("%d", &graph[i][j]);
        }
    }

    hamiltonianCycle(graph, totalVertices);

    return 0;
}
