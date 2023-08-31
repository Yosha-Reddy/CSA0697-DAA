#include <stdio.h>
#include <stdbool.h>
void generateSubsets(int arr[], int n, bool subset[], int index, int targetSum, int currentSum) {
    if (index == n) {
        if (currentSum == targetSum) {
            printf("Subset with target sum %d: {", targetSum);
            for (int i = 0; i < n; i++) {
                if (subset[i]) {
                    printf(" %d", arr[i]);
                }
            }
            printf(" }\n");
        }
        return;
    }
    subset[index] = true;
    generateSubsets(arr, n, subset, index + 1, targetSum, currentSum + arr[index]);
    subset[index] = false;
    generateSubsets(arr, n, subset, index + 1, targetSum, currentSum);
}
int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the elements:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    int targetSum;
    printf("Enter the target sum: ");
    scanf("%d", &targetSum);
    bool subset[n];
    generateSubsets(arr, n, subset, 0, targetSum, 0);
    return 0;
}
