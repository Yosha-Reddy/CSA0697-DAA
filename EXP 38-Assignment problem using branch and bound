#include <stdio.h>
#include <stdbool.h>
#define MAX_SIZE 100
#define INF 9999
int numWorkers;
int numJobs;
int costMatrix[MAX_SIZE][MAX_SIZE];
bool assigned[MAX_SIZE];
int minCost = INF;
int finalAssignment[MAX_SIZE];
void printAssignment() {
    printf("Optimal Assignment:\n");
    for (int i = 0; i < numWorkers; i++) {
        printf("Worker %d -> Job %d\n", i + 1, finalAssignment[i] + 1);
    }
}
void updateMinCost(int assignment[MAX_SIZE]) {
    int totalCost = 0;
    for (int i = 0; i < numWorkers; i++) {
        totalCost += costMatrix[i][assignment[i]];
    }

    if (totalCost < minCost) {
        minCost = totalCost;
        for (int i = 0; i < numWorkers; i++) {
            finalAssignment[i] = assignment[i];
        }
    }
}
void branchAndBound(int worker, int currentCost, int assignment[MAX_SIZE]) {
    if (worker == numWorkers) {
        updateMinCost(assignment);
        return;
    }
    for (int job = 0; job < numJobs; job++) {
        if (!assigned[job]) {
            int newCost = currentCost + costMatrix[worker][job];

            if (newCost < minCost) {
                assigned[job] = true;
                assignment[worker] = job;

                branchAndBound(worker + 1, newCost, assignment);

                assigned[job] = false;
            }
        }
    }
}
int main() {
    printf("Enter the number of workers: ");
    scanf("%d", &numWorkers);
    printf("Enter the number of jobs: ");
    scanf("%d", &numJobs);
    printf("Enter the cost matrix (%d x %d):\n", numWorkers, numJobs);
    for (int i = 0; i < numWorkers; i++) {
        for (int j = 0; j < numJobs; j++) {
            scanf("%d", &costMatrix[i][j]);
        }
    }
    int assignment[MAX_SIZE];
    for (int i = 0; i < numWorkers; i++) {
        assigned[i] = false;
    }
    branchAndBound(0, 0, assignment);
    printf("Minimum Cost: %d\n", minCost);
    printAssignment();
    return 0;
}
