#include <stdio.h>
#include <limits.h>
#define MAX_KEYS 10
int optimalCostBST(int keys[], int freq[], int n) {
    int cost[n][n];
    for (int i = 0; i < n; i++) {
        cost[i][i] = freq[i];
    }
    for (int chain_len = 2; chain_len <= n; chain_len++) {
        for (int start = 0; start < n - chain_len + 1; start++) {
            int end = start + chain_len - 1;
            cost[start][end] = INT_MAX;
            for (int root = start; root <= end; root++) {
                int left_cost = (root > start) ? cost[start][root - 1] : 0;
                int right_cost = (root < end) ? cost[root + 1][end] : 0;
                int current_cost = left_cost + right_cost + freq[root];
                if (current_cost < cost[start][end]) {
                    cost[start][end] = current_cost;
                }
            }
        }
    }

    return cost[0][n - 1];
}
int main() {
    int keys[MAX_KEYS], freq[MAX_KEYS];
    int n;
    printf("Enter the number of keys (maximum %d): ", MAX_KEYS);
    scanf("%d", &n);
    printf("Enter the keys in sorted order:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &keys[i]);
    }
    printf("Enter the frequencies of the keys:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &freq[i]);
    }
    int optimal_cost = optimalCostBST(keys, freq, n);
    printf("Optimal cost of the Binary Search Tree is: %d\n", optimal_cost);
    return 0;
}
