# Stat_991
Question 1 assignment 
#include <stdio.h>

// Function to sort an array (for median calculation)
void sort(int arr[], int n) {
    int temp;
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] > arr[j]) {
                temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}

// Function to calculate mean
float mean(int arr[], int n) {
    int sum = 0;
    for (int i = 0; i < n; i++)
        sum += arr[i];
    return (float)sum / n;
}

// Function to calculate median
float median(int arr[], int n) {
    sort(arr, n);
    if (n % 2 == 0)
        return (arr[n / 2 - 1] + arr[n / 2]) / 2.0;
    else
        return arr[n / 2];
}

// Function to calculate mode
int mode(int arr[], int n) {
    int maxValue = 0, maxCount = 0;
    for (int i = 0; i < n; ++i) {
        int count = 0;
        for (int j = 0; j < n; ++j) {
            if (arr[j] == arr[i])
                ++count;
        }
        if (count > maxCount) {
            maxCount = count;
            maxValue = arr[i];
        }
    }
    return maxValue;
}

// Function to calculate weighted mean
float weightedMean(int values[], int weights[], int n) {
    int sumV = 0, sumW = 0;
    for (int i = 0; i < n; i++) {
        sumV += values[i] * weights[i];
        sumW += weights[i];
    }
    return (float)sumV / sumW;
}

int main() {
    int n;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    int data[n], weights[n];

    printf("Enter %d data values: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &data[i]);

    printf("Enter %d corresponding weights: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &weights[i]);

    printf("\n--- Results ---\n");
    printf("Mean: %.2f\n", mean(data, n));
    printf("Median: %.2f\n", median(data, n));
    printf("Mode: %d\n", mode(data, n));
    printf("Weighted Mean: %.2f\n", weightedMean(data, weights, n));

    return 0;
}
